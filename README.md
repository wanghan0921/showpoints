### 1.BOM 浏览器对象模型
```js
window.alter('hello');
window.loaction.herf = 'www.baidu.com'
```

### 2.代码自动补全
```js
node XXX + Tab键
```

### 3.Object.assgin 不要和 new formData()一起用

我们会用axios的预处理为每一次请求都带上特定的参数用Object.assgin对对象进行深拷贝， 但是如果是上传图片或文件时， 就不要这样用， 否则会出现问题
