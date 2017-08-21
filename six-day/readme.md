# javascript 💪第六天

## 项目目的
对于ajax的初步认识


## 知识点总结（数组的总结）
1. **ajax回顾的使用**

   对于楼主刚刚学习ajax的时候，还是通过XML获取接口数据，当时流行ajax四部曲

   ```javascript
   //1. 初始化XMLHttpRequest()
   let xml = new XMLHttpRequest()

   //2. 请求完数据做什么
   xml.onload = function() {
     
   }
   //3. 请求api和数据
   xml.open('方法','接口')
   //4. 发送请求
   xml.send()  //post的参数也是在这里发送
   ```

2. **fetch()基本语法**

   >这是一个实验中的方法，但是楼主相信它一定之后会取代xml获取接口的方法。

   * **fetch()方法返回的是一个promise**，对于请求的数据，通过数据流的方式传输，所以我们需要通过它自带的方法来处理返回的数据。

     `response.blob()` :转换二进制流成真正的`**图片**`

     `response.json()`: 处理**json格式**的数据

     `response.text():` 处理**文本**数据

     `response.formData():` 处理**表格**数据

     ```javascript
     // 获取图片的
     var myImage = document.querySelector('img');
     fetch('https://avatars1.githubusercontent.com/u/22970787?v=4&s=460')
     .then(function(response) {
       return response.blob();
     })
     .then(function(myBlob) {
       var objectURL = URL.createObjectURL(myBlob);
       myImage.src = objectURL;
     });
     // 1. 请求了接口返回一个可以处理数据的response
     // 2. 可以根据原型链上面的方法来处理,如blob()
     // 3. status返回状态码 
     // 4. 请求是否成功 reponse.ok
     ```

     ![fetch](C:\Users\Z7\Desktop\fetch.png)

     ```javascript
     // 请求json数据
     fetch('https://gist.githubusercontent.com/soyaine/81399bb2b24ca1bb5313e1985533c640/raw/bdf7df2cbcf70706c4a5e51a7dfb8c933ed78878/TangPoetry.json').then(function(response) {
       if(response.ok) {
         response.json().then(function(data) {
           console.log(typeof data)
     	  console.log(data)
         });
       } else {
         console.log('Network response was not ok.');
       }
     })
     .catch(function(error) {
       console.log('There has been a problem with your fetch operation: ' + error.message);
     });
     ```

   * **错误处理：** fetch() 对于错误的处理，除了网络异常，[`fetch()`](https://developer.mozilla.org/zh-CN/docs/Web/API/GlobalFetch/fetch) promise 将会 reject，带上一个 [`TypeError`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypeError) 对象，其他的都不会返回一个错误信息，但是我们可以通过`response.ok`或者`response.status`来进行细致的处理

     ![错误提示](C:\Users\Z7\Desktop\错误提示.png)

   * Headers()  和 Request() 构造函数可以对请求头和请求参数进行对象的配置

     ```javascript
     // 请求头
     var content = "Hello World";
     var myHeaders = new Headers();
     myHeaders.append("Content-Type", "text/plain");
     myHeaders.append("Content-Length", content.length.toString());
     myHeaders.append("X-Custom-Header", "ProcessThisImmediately");

     // 请求参数
     var myInit = { method: 'GET',
                    headers: myHeaders,
                    mode: 'cors',
                    cache: 'default' };
     var myRequest = new Request('flowers.jpg', myInit);
     ```

3.  **合并数组**

   ES6 添加拓展运算符，对于数组的操作可以更加的方便

   ```javascript
   var arr = []
   var arr2 = [1,3,4,6]
   // es5 添加数组
   Array.prototype.push.apply(arr,arr2)
   // es6通过拓展运算符
   arr.push(...arr2)
   // 获取数组中的最大项
   Math.max.apply(null,arr2)  //es5
   Math.max(...arr2)
   ```

## 黑科技

#### 一、处理数据的正则

> 1234567522  =>1,234,567, 522
>
> 234567522  =>  234,567, 522

```javascript
var test1 = '1234567890'
var format = test1.replace(/\B(?=(\d{3})+(?!\d))/g, ',')

console.log(format) // 1,234,567,890

// number
function numberWithCommas(x) {
  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}
```

#### 二、单行写一个评级组件

```javascript
const rate = 1
"★★★★★☆☆☆☆☆".slice(5-rate,10-rate)
```

[参考链接](https://github.com/jawil/blog/issues/24)

#### 在这个好高骛远的时代，坚持JavaScript原生30天**



