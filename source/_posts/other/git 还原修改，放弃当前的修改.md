---
title: git 还原修改，放弃当前的修改

index_img: 
lazyload: true
categories:
- 前端周边
tags:
- git



---













还原有三种情况：
1. 只是修改了文件，`没有任何 git 操作`
2. 修改了文件，并提交到暂存区（即：`编辑之后，进行git add 但没有 git commit -m "留言xxx"`）
3. 修改了文件，并提交到仓库区（即：`编辑之后，进行git add 并且 git commit -m "留言xxx"`）


**如果是情况1：**

```javascript
git checkout -- aaa.html 			// 指定还原`aaa.html`文件
git checkout -- * 					// 还原所有文件
```


**如果是情况2：**

```javascript
git log --oneline            // 可以省略
git reset HEAD               // 回退到当前版本
git checkout -- aaa.html
```



**如果是情况3：**

```javascript
git log --oneline   			 // 可以省略
git reset HEAD^    				 // 回退到上一个版本，注意看HEAD后面有个 ^						HEAD^ 是回退到上个版本					HEAD^^ 是回退到上上个版本					HEAD~数字 是回退到数字个版本
git checkout -- aaa.html
```
