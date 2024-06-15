---
title: 基于elementUI封装的表格分页一体组件【拿来即用】

index_img: https://img-blog.csdnimg.cn/7423853cb4334e7c8b89a7f927eb97fa.png
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2
- elementUI


---













![](https://img-blog.csdnimg.cn/7423853cb4334e7c8b89a7f927eb97fa.png)

# 内容说明
1. 表格
2. 表格左上角插槽
3. 表格右上角插槽
4. 分页
5. 预设了导出、打印事件





### 拆箱即用

```html
<template>
  <div class="">
    <div class="d-flex justify-content-between align-items-end">
      <el-button-group class="d-flex functions">
        <slot name="left"></slot>
        <el-dropdown :disabled="data.length < 1" v-if="derive && (total > pageSize)" trigger="click" @command="exporting">
          <el-button :size="size">
            导出<i class="el-icon-arrow-down el-icon--right"></i>
          </el-button>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item command="1">导出本页</el-dropdown-item>
            <el-dropdown-item command="2">导出全部</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <el-button v-if="derive && (total < pageSize)" :disabled="data.length < 1" :size="size"
          @click="exporting('1')">导出</el-button>
        <el-dropdown :disabled="data.length < 1" v-if="$listeners.printing && (total > pageSize)" trigger="click"
          @command="printing">
          <el-button :size="size">
            打印<i class="el-icon-arrow-down el-icon--right"></i>
          </el-button>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item command="1">打印本页</el-dropdown-item>
            <el-dropdown-item command="2">打印全部</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <el-button v-if="$listeners.printing && (total < pageSize)" :disabled="data.length < 1" :size="size"
          @click="printing('1')">打印</el-button>
      </el-button-group>
      <el-button-group>
        <slot name="right"></slot>
      </el-button-group>
    </div>
    <el-table ref="table" :row-class-name="rowClassName" :size="size" :data="data"
      :[olyHeight]="height || maxHeight || '400'" :border="border" :row-key="rowKey" :empty-text="emptyText"
      v-loading="loading" :show-summary="showSummary" :summary-method="summaryMethod" tooltip-effect="dark"
      highlight-current-row @row-click="rowClick" @cell-click="cellClick" @select="select" @select-all="selectAll"
      @selection-change="selectionChange" element-loading-text="拼命加载中" element-loading-spinner="el-icon-loading"
      element-loading-background="rgba(0, 0, 0, 0.8)" @row-dblclick="rowDblclick">
      <el-table-column v-if="showSelection" fixed="left" :reserve-selection="reserveSelection" type="selection"
        min-width="60" :selectable="selecteisDisabled">
      </el-table-column>
      <el-table-column v-if="showIndex" fixed="left" label="序号" min-width="50">
        <template slot-scope="scope">
          {{ pageSize * (currentPage - 1) + (scope.$index + 1) }}
        </template>
      </el-table-column>
      <slot name="columns"></slot>
    </el-table>
    <el-pagination class="text-end mt-3" v-if="$listeners['current-change']" @size-change="dataSizeChange"
      @current-change="handleCurrentChange" :page-sizes="[$tableDataSize, 20, 30, 50]" :page-size="pageSize"
      :disabled="total <= 0 || loading" :current-page="currentPage" layout="total, sizes, prev, pager, next, jumper"
      :total="total">
    </el-pagination>
  </div>
</template>

<script>
/**
 * @author        全易
 * @time          2021-12-28 13:26:08  星期二
 * @description   自定义的表格，使用方式同elementUI。属性、方法、事件参考elementUI文档
 **/
import { exportExcel } from "@/utils/export-file.js";

export default {
  name: "custom-table",
  data() {
    return {
      pageNow: 1
    };
  },
  props: {
    name: {
      type: String,
    },
    // 显示序号列
    showIndex: {
      type: Boolean,
      default: false,
    },
    data: {
      type: Array,
      default: () => {
        return [];
      },
    },
    loading: {
      type: Boolean,
      default: false,
    },
    size: {
      type: String,
      default: "small",
    },
    emptyText: {
      type: String,
    },
    border: {
      type: Boolean,
      default: true,
    },
    rowKey: {
      type: [String, Number],
    },
    height: {
      type: [String, Number],
    },
    maxHeight: {
      type: [String, Number],
    },
    total: {
      type: Number,
      default: 0,
    },
    pageSize: {
      type: Number,
      default() {
        return this.$tableDataSize;
      },
    },
    currentPage: {
      type: Number,
      default() {
        return 1;
      },
    },
    showSummary: {
      type: Boolean,
      default: false,
    },
    summaryMethod: {
      type: Function
    },
    reserveSelection: {
      type: Boolean,
      default: true
    },
    // 返回值用来决定这一行的 CheckBox 是否可以勾选
    selecteisDisabled: {
      type: Function
    },
    rowClassName: {
      type: Function
    },
    derive: {
      type: Function,
      default: null
    }
  },
  watch: {
    data(now, old) {
      const that = this;
      this.$nextTick(() => {
        that.doLayout(); // 为了解决行错位问题
      });
    },
  },
  computed: {
    showSelection() {
      return this.$listeners["select"] || this.$listeners["selection-change"];
    },
    olyHeight() {
      // 因为elementUI不能 height 和 max-height 同时存在，所以采用动态属性
      // console.log("height：", this.height, "maxHeight：", this.maxHeight);
      return this.height ? "height" : "max-height";
    },
  },
  activated() {
    this.doLayout();
  },
  methods: {
    // 页量
    dataSizeChange(val) {
      console.log(`每页 ${val} 条`);
      this.$emit("size-change", val);
    },
    // 翻页
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
      this.$emit("current-change", val);
    },
    // 选择数据
    select(selection, row) {
      // console.log(election, row);
      this.$emit("select", selection, row);
      this.doLayout();
    },
    // 选择数据
    selectionChange(selection) {
      // console.log(selection);
      this.$emit("selection-change", selection);
      this.doLayout();
    },
    // 全选数据
    selectAll(selection) {
      console.log(selection);
      this.$emit("select-all", selection);
      this.doLayout();
    },
    // 清空选择
    clearSelection() {
      this.$refs.table.clearSelection();
      this.doLayout();
    },
    // 全选
    toggleAllSelection() {
      this.$refs.table.toggleAllSelection();
      this.doLayout();
    },
    // 选择数据
    toggleRowSelection(row = [], selected = true) {
      this.$refs.table.toggleRowSelection(row, selected);
      this.doLayout();
    },
    // 单选数据
    setCurrentRow(row) {
      this.$refs.table.setCurrentRow(row);
      this.doLayout();
    },
    // 点击行
    rowClick(row, column, event) {
      // console.log(row, column, event);
      this.$emit("row-click", row, column, event);
      this.doLayout();
    },
    // 点击单元格
    cellClick(row, column, cell, event) {
      this.$emit("cell-click", row, column, cell, event);
      this.doLayout();
    },
    // 双击行
    rowDblclick(row, column, event) {
      this.$emit("row-dblclick", row, column, event);
    },
    // 导出表格
    exporting(command) {
      if (this.total < 1) {
        this.$message.warning("无数据可导");
        return false;
      }

      if (command === "1" || (command === "2" && this.total < 3000)) {
        this.exportingExcel(command);
      } else {
        this.$message.success("即将打开微信对话，请注意您的微信软件")
        window.open(process.env.VUE_APP_DEPARTMENT_SERVICE, "_blank", "location=no, status=no, menubar=no");
      }

      this.doLayout();
    },
    // 执行导出表格
    exportingExcel(command) {
      const title = this.name || this.$route.meta.menuName + "表";
      const notify = Notification.permission === "granted" ? new Notification("开始下载", { body: title }) : this.$notify.info({ title: "开始下载" });

      this.derive(command).then(data => {
        if (data) {
          exportExcel(data, title);
          Notification.permission === "granted" ? new Notification("下载成功", { body: title }) : this.$notify.success({ title: "下载成功" });
        } else {
          Notification.permission === "granted" ? new Notification("下载失败", { body: title }) : this.$notify.error({ title: "下载失败" });
        }
      }).catch(() => {
        Notification.permission === "granted" ? new Notification("下载失败", { body: title }) : this.$notify.error({ title: "下载失败" });
      }).finally(() => {
        notify.close();
      })
    },
    // 打印表格数据
    printing(command) {
      if (this.total < 1) {
        return this.$message.info("无数据打印");
      }

      this.$emit("printing", command);
      this.doLayout();
    },
    // 重载表格
    doLayout() {
      this.$refs.table.doLayout();
    },
    // 获取列
    getColumns() {
      let columns = [];
      (function flattening(data) {
        data.map((item) => {
          if (item.$children) {
            flattening(item.$children); // 递归执行
          }
          if (item.label && item.prop) {
            columns.push({
              label: (item.$parent.label || "") + item.label,
              prop: item.prop,
            });
          }
        });
      })(this.$refs.table.$children);
      // console.log(columns);
      return columns;
    },
    exportExcel
  },
};
</script>

<style lang="less" scoped>

</style>
```

