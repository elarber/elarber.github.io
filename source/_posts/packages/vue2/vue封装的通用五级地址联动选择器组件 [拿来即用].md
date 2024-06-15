---
title: vue封装的通用五级地址联动选择器组件 [拿来即用]

index_img: https://img-blog.csdnimg.cn/12681139cfbf4a2aa4febf3f92a42cbe.gif
lazyload: true
categories:
- vue2
- 拿来主义
tags:
- vue2



---












> 数据来源：[https://api.muxiaoguo.cn/doc/cityLinkage.html](https://api.muxiaoguo.cn/doc/cityLinkage.html)
> UI依赖：[https://element.eleme.cn/#/zh-CN/component/select](https://element.eleme.cn/#/zh-CN/component/select)
> CSS依赖：[http://lesscss.cn/](http://lesscss.cn/)

# 效果：
![](https://img-blog.csdnimg.cn/12681139cfbf4a2aa4febf3f92a42cbe.gif#pic_center)


# 调用：
组件源码在最下面
![](https://img-blog.csdnimg.cn/77af6aed96ea40ef98795078129b68a5.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)

# 清除验证：
![](https://img-blog.csdnimg.cn/2f164ee2ab2b41349d3e22c9a941005a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)

# 提交数据
![](https://img-blog.csdnimg.cn/d7dcf65e86154cd18033a60c0fcd564e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)


# 得到的返回值：
![](https://img-blog.csdnimg.cn/326e0734c27b463fa49f825cb9c2b158.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5YWo5piT,size_20,color_FFFFFF,t_70,g_se,x_16)


# 组件配置说明：
| 属性 | 说明 | 必传 | 类型 |  默认  |
|--|--|--|--|--|
| labelWidth | 表单的label宽度 |   否 | Number  | 95 |
| showRemark | 是否需要地址的备注 |   否 | Boolean  |  false |
| col | 表单的一个输入组宽度，按照elemenUI的占位 | 否 | Number  |  6 |
| data | 回显的数据 | 回显时必传  |  Object |  {} |


# 回显数据规则：
必须是对应：

```javascript
{
  provinces: "",
  city: "",
  district: "",
  towns: "",
  village: "",
  buildNo: "",
  unitNo: "",
  houseNo: "",
  remark: ""
}
```




# 组件源码
拿来即用
```html
 <template>
  <el-form
    :model="forms"
    :label-width="labelWidth + 'px'"
    :rules="rules"
    ref="forms"
  >
    <el-row :gutter="10">
      <el-col :span="col">
        <el-form-item
          :label="labelWidth === 0 ? '' : '省/自治区/直辖市'"
          prop="provinces"
        >
          <el-select
            clearable
            filterable
            v-model="forms.provinces"
            @change="selection('1', $event,'0')"
            :placeholder="labelWidth === 0 ? '省/自治区' : ''"
          >
            <el-option
              v-for="item in dropdowns.provinces"
              :key="item.code"
              :label="item.name"
              :value="item.code"
            ></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="col">
        <el-form-item :label="labelWidth === 0 ? '' : '市/区'" prop="city">
          <el-select
            clearable
            filterable
            v-model="forms.city"
            no-data-text="请选择省/自治区"
            @change="selection('2', $event,'0')"
            :placeholder="labelWidth === 0 ? '市/区' : ''"
          >
            <el-option
              v-for="item in dropdowns.city"
              :key="item.code"
              :label="item.name"
              :value="item.code"
            ></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="col">
        <el-form-item :label="labelWidth === 0 ? '' : '区/县'" prop="district">
          <el-select
            clearable
            filterable
            v-model="forms.district"
            no-data-text="请选择市/区"
            @change="selection('3', $event,'0')"
            :placeholder="labelWidth === 0 ? '区/县' : ''"
          >
            <el-option
              v-for="item in dropdowns.district"
              :key="item.code"
              :label="item.name"
              :value="item.code"
            ></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="col">
        <el-form-item :label="labelWidth === 0 ? '' : '乡镇/街道'" prop="towns">
          <el-select
            clearable
            filterable
            v-model="forms.towns"
            no-data-text="请选择区/县"
            @change="selection('4', $event,'0')"
            :placeholder="labelWidth === 0 ? '乡镇/街道' : ''"
          >
            <el-option
              v-for="item in dropdowns.towns"
              :key="item.code"
              :label="item.name"
              :value="item.code"
            ></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="col">
        <el-form-item
          :label="labelWidth === 0 ? '' : '村/会/庄'"
          prop="village"
        >
          <el-select
            clearable
            filterable
            v-model="forms.village"
            placeholder=""
          >
            <el-option
              v-for="item in dropdowns.village"
              :key="item.code"
              :label="item.name"
              :value="item.code"
            ></el-option>
          </el-select>
        </el-form-item>
      </el-col>
      <el-col :span="col">
        <el-form-item
          class="specific"
          :label="labelWidth === 0 ? '' : '具体地址'"
        >
          <el-input
            clearable
            v-model.number="forms.buildNo"
            :placeholder="labelWidth === 0 ? '楼号' : ''"
          >
            <template v-if="labelWidth > 0" slot="append">号楼</template>
          </el-input>
          <el-input
            clearable
            v-model.number="forms.unitNo"
            :placeholder="labelWidth === 0 ? '单元' : ''"
          >
            <template v-if="labelWidth > 0" slot="append"
              >单元</template
            ></el-input
          >
          <el-input
            clearable
            v-model.number="forms.houseNo"
            :placeholder="labelWidth === 0 ? '门牌号' : ''"
          >
            <template v-if="labelWidth > 0" slot="append"
              >室</template
            ></el-input
          >
        </el-form-item>
      </el-col>
      <el-col v-if="showRemark" :span="col">
        <el-form-item :label="labelWidth === 0 ? '' : '地址备注'">
          <el-input
            v-model="forms.remark"
            :placeholder="labelWidth === 0 ? '地址备注' : ''"
          ></el-input>
        </el-form-item>
      </el-col>
    </el-row>
  </el-form>
</template>

<script>
/**
 * @author        全易
 * @time          2021-08-13 17:12:59  星期五
 * @description   地址选择器
 */

export default {
  name: "es-address",
  props: {
    labelWidth: {
      type: Number,
      default: 95,
    },
    showRemark: {
      type: Boolean,
      default: false,
    },
    col: {
      type: Number,
      default: 6,
    },
    data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  watch: {
    data(now, old) {
      // console.log(now);
      this.forms = now;

      for (let i = 1; i < 4; i++) {
        // i必须转字符串
        switch (i) {
          case 1:
            this.selection(i + "", now.provinces);
            break;
          case 2:
            this.selection(i + "", now.city);
            break;
          case 3:
            this.selection(i + "", now.district);
            break;
          case 4:
            this.selection(i + "", now.village);
            break;
        }
      }
    },
  },
  data() {
    return {
      dropdowns: {
        provinces: [],
        city: [],
        district: [],
        towns: [],
        village: [],
      },
      rules: {
        provinces: [
          {
            required: true,
            message: "请选择省/自治区/直辖市",
            trigger: "change",
          },
        ],
        city: [{ required: true, message: "请选择市/区", trigger: "change" }],
        district: [
          { required: true, message: "请选择区/县", trigger: "change" },
        ],
        towns: [
          { required: true, message: "请选择乡镇/街道", trigger: "change" },
        ],
        village: [
          { required: true, message: "请选择村/会/庄", trigger: "change" },
        ],
      },
      forms: {
        provinces: "",
        city: "",
        district: "",
        towns: "",
        village: "",
        buildNo: "",
        unitNo: "",
        houseNo: "",
        remark: "",
      },
    };
  },
  created() {
    this.selection("0", "getCity");
  },
  methods: {
    selection(level, code) {
      // console.log(level, code);
      fetch(`https://api.muxiaoguo.cn/api/cityLinkage?id=${code}`) // 如果不能用了，就自己找个接口吧
        .then((response) => {
          return response.json();
        })
        .then((result) => {
          // console.log(result);
          switch (level) {
            case "0":
              this.dropdowns.provinces = result.data;
              break;
            case "1":
              this.dropdowns.city = result.data;
         
                  this.dropdowns.district = [];
	              this.dropdowns.towns = [];
	              this.dropdowns.village = [];
	              this.forms.city = "";
	              this.forms.district = "";
	              this.forms.towns = "";
	              this.forms.village = "";
              
              break;
            case "2":
              this.dropdowns.district = result.data;
             
                this.dropdowns.towns = [];
	            this.dropdowns.village = [];
	            this.forms.district = "";
	            this.forms.towns = "";
	            this.forms.village = "";
              
              break;
            case "3":
              this.dropdowns.towns = result.data;
            
                 this.dropdowns.village = [];
	             this.forms.towns = "";
	             this.forms.village = "";
              
              break;
            case "4":
              this.dropdowns.village = result.data;
             
              this.forms.village = "";
            
              break;
          }
        });
    },
    submit() {
      this.$refs["forms"].validate((valid) => {
        if (valid) {
          this.$emit("submit", this.forms);
        }
      });
    },
    resetFields() {
      this.$refs["forms"].resetFields();
      for (let i in this.forms) {
        this.forms[i] = "";
      }
    },
  },
};
</script>

<style lang="less" scoped>
/deep/.specific {
  .el-form-item__content {
    display: grid;
    grid-template-columns: auto auto auto;
    gap: 10px;
    justify-content: space-between;
    &::after,
    &::before {
      display: none;
    }
  }
}
</style>
```



# 地址数据来源：
> [https://github.com/modood/Administrative-divisions-of-China](https://github.com/modood/Administrative-divisions-of-China)
> [https://gitee.com/modood/Administrative-divisions-of-China](https://gitee.com/modood/Administrative-divisions-of-China)








# 三级一体选择器
> 使用elementUI的Cascader级联选择器进行地址三级一体选择
> **[https://blog.csdn.net/qq_42618566/article/details/115403544](https://blog.csdn.net/qq_42618566/article/details/115403544)**


