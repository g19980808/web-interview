## html5

canvas

是 HTML5 新增的元素，可用于通过使用JavaScript中的脚本来绘制图形

```javascript
    var canvas = document.getElementById('box');
    var ctx = canvas.getContext('2d');
    // 填充一个矩形（实心）
    ctx.fillStyle = "pink"
    ctx.strokeStyle = "green"
    ctx.lineWidth = 10
    ctx.lineJoin = "bevel"
    ctx.fillRect(10, 10, 100, 100)

    // 填充一个边框矩形
    ctx.strokeRect(110, 110,100, 100)

    // 清除一个矩形边框
    ctx.clearRect(20, 20,50, 50)
```



Canvas 和SVG区别



1. Canvas 主要是用笔刷来绘制 2D 图形
2. SVG 主要是用标签来绘制不规则矢量图
3. 相同点：都是主要用来画 2D 图形
4. 不同点：Canvas 画的是位图，SVG 画的是矢量图
5. 不同点：SVG 节点过多时渲染慢，Canvas 性能更好一点，但写起来更复杂
6. 不同点：SVG 支持分层和事件，Canvas 不支持，但是可以用库实现