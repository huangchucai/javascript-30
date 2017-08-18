# javascript 💪第六天

## 项目目的
对于ajax的初步认识


## 知识点总结（数组的总结）
1. fetch()的使用

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

2. `transitionend`事件

   **关键点总结：**通过`transitionend`事件的事件处理函数e，来获取对应的引发transition的属性。`e.propertyName`

   ```javascript
   panel.addEventListener('transitionend',(e) => {
     console.log(e.propertyName)
   })
   ```

3. dom的classList

   **关键点总结：**通过自带的`classList`属性控制对类的切换。

   ```javascript
   this.classList.toggle('open-active')
   ```


#### **在这个好高骛远的时代，坚持JavaScript原生30天**
