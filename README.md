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















