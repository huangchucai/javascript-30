# javascript 💪第五天

## 项目目的
实现一个类似于百叶窗的效果，点击对应的图片放大，并且同时上下2个方向的文字出现，同时其他图片缩小。


## 知识点总结（数组的总结）
1. flex总结

   ![图片来源网络](http://upload-images.jianshu.io/upload_images/2166980-a3a872b9fb50bd86.png?imageMogr2/auto-orient/strip%7CimageView2/2)

   * 父容器 （`flex-direction`,`align-items`,`justify-content`,`flex-wrap`, `align-cotents`）
   * 自容器  (`flex-grow`, `flex-strink`,`flex-basis`,`flex`,`align-self`)

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
