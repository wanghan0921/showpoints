### 1.BOM 浏览器对象模型
```js
window.alter('hello');
window.loaction.herf = 'www.baidu.com'
```

### 2.代码自动补全
```js
XXX + Tab键
```

### 3.Object.assgin 不要和 new formData()一起用

我们会用axios的预处理为每一次请求都带上特定的参数用Object.assgin对对象进行浅拷贝， 但是如果是上传图片或文件时， 就不要这样用， 否则会出现问题

### 4.cmd
```js
ls // 显示文件夹里面的文件
cd ../  //去某个文件夹下
code ../ 用vscode打开
```

### 5.OOP 面向对象编程

以对象来划分功能
+ 封装性
+ 继承性
+ 多态性(在不同的时候,呈现不同的功能)


### 6.Node.js中相对路径相对的是谁的路径？

终端中的所处的路径 ， 不是js文件所在的路径


### 7.原生js中onclick和click的区别

+ onclick是调用绑定的事件，不会触发默认行为， 例如a标签的herf就不会触发
+ click就相当于用代码去模拟点击 ， 都会触发


### 8. express

### 9.body-parser 中间件 ， 获取post请求传过来的数据-文本

### 10.multer 获取post请求传过来的文件 - fromData


### 9. insertAdjacentHTML()
[文档](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/insertAdjacentHTML)

需求: 新增元素

以前的做法:

  动态创建元素createElement, 但是元素里面内容较多, 需要innerHtml赋值, 再appendChild追加到父元素里面
 
高级一点的做法:

  利用insertAdjacentHTML()可以直接把字符串格式的元素添加到父元素中
  
```js
const div = `<div class="main"><span>1111</span></div>`

// beforeend 是插入的位置, 有四个可选项
this.ui.insertAdjacentHTML('beforeend', div)
```
  
  
### 10. middleware 中间件

在请求和响应之间， 执行的回调函数


### 11. Uncaught (in promise)

解决 : 跨域问题


### 12. stopPropagation()

阻止冒泡


### 13. 双击 ondblclick()

### 14. 禁止选中文字

```js
window.getSelection ? window.getSelection().removerAllRanges() : document.selection.empty()
```


### 15. string.trim() 去除字符串两侧的空格

```js

let str = '  wanghan   '
let new_str = str.trim()
console.log(new_str)   // wanghan
```


### 16. Object.keys() 用于获取对象的所有的属性

```js
object.keys(obj)
```

+ 效果类似与for...in
+ 返回一个由属性名组成的数组

































