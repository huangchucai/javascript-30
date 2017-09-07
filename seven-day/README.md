# javascript 💪第七天
## 项目目的
初步熟悉canvas的使用

### HTML5 => canvas
1. 声明一个canvas标签，必须添加`width` `height`
```html
<canvas width="600" height="300" id="draw"></canvas> 
```
2. 基本属性
```javascript
let canvas = document.querySelector('#draw');
let cxt = canvas.getContext('2d');
cxt.lineCap // 开始的形状
cxt.lineJoin // 结束的形状
cxt.lineWidth // 线条的大小
cxt.strokeStyle // 线条的颜色
```
3. 开始绘画
```javascript
cxt.beginPath();
cxt.moveTo(lastX, lastY);
cxt.lineTo(e.offsetX, e.offsetY);
cxt.stroke();
```

## 额外知识点
### 事件处理event
* 可以通过`e.offsetX`,`e.offsetY`获取对应的鼠标位置
### 鼠标事件
* mousedown 鼠标按下的瞬间执行
* mousemove 鼠标移动的时候执行
* mouseup   鼠标抬起的时候执行
* mouseout  鼠标离开画布的时候执行