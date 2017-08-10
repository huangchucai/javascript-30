### javascript 第三天

#### 知识点总结
1. `:root`属性设置根元素html的样式，优先级还要高于通过html标签设置。通常和`css`变量一起使用

   [MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root)

   ```css
   :root{
     font-size: 10px;
     --base: #ffc600;
     --spacing: 10px;
     --blur: 10px;
   }
   ```

2. `css变量`。通过带有前缀 -- 的属性名编写。使用var()全局调用。

   [MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/--*)

   ```css
   </*css变量*/>
   --somekeyword: left;
   --somecolor: #0000ff;
   --somecomplexvalue: 3px 6px rgb(20, 32, 54);
   </*css变量调用*/>
   h1{
     color: var(--somekeyword);
   }
   ```

3. 获取自定义属性`dataset`。可以通过el.dataset获取元素的自定义属性，得到的是一个对象集合。

   ```html
   <div id="user" data-id="1234567890" data-user="johndoe" data-date-of-birth>John Doe</div>

   var el = document.querySelector('#user');
   el.dataset  //{id: "1234567890", user: "johndoe", dateOfBirth: ""}
   ```

4. `document.documentElement`获取html元素

5. `dom.style.setProperty(propertyName, value, priority);`设置元素css的属性

   [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleDeclaration/setProperty)

   ```javascript
   // 设置html的样式
   document.documentElement.style.setProperty('fontSize','10px')
   // 设置id=user的属性
   var el = document.querySelector('#user');
   el.style.setProperty('color','red');
   ```

6. `http://unsplash.it/1500/1000?image=881&blur=50` blur设置模糊

**在这个好高骛远的时代，坚持JavaScript原生30天**
