#webdev 

# Initialize
```html
<canvas id="canvas"></canvas>


<script>
	const canvas = document.getElementById("canvas");
	const context = canvas.getContext("2d");
</script>
```


# Draw Loop

1. Clear canvas
2. Draw Object
3. Repeat

## Clear canvas

```js
context.clearRect(x,y,w,h)
```

## Draw Object

```js
//fill obj
context.fillStyle = "red";
context.fillRect(x,y,w,h)

//stroke obj
context.strokeStyle = "red";
context.linewidth = 3;
context.strokeRect(x,y,w,h);

//path
context.beginPath();
context.arc(cx,cy,r,startAngle,endAngle,counterClockwise);
context.moveTo(x,y);
context.lineTo(x,y);
context.stroke(); //can use context.fill to fill the area

//fill text
context.font = "20px Arial";
context.fillText("Hey yo",x,y);

//stroke text
context.strokeStyle = "red";
context.lineWidth = 2;
context.font = "bold 40px Georgia";
context.strokeText("Hollow text",x,y);
```

>[!Tip] Check if a point is in an area
>`context.isPointInPath(x,y)` 

>[!Tip] Check Text width
>`context.measureText()`

## Repeat

Using the `requestAnimationFrame()` to draw a new frame, it make sure the code run in 60 fps.

```js
function doFrame(){
	context.clearRect(...);
	//Update the content
	requestAnimationFrame(doFrame);
}

requestAnimationFrame(doFrame);
```

Controlling the update speed
```js
let last = performance.now(); //current time

function doFrame(now){
	if(now-last >= timegap){
		//...
		last = now;
	}
}

requestAnimationFrame(doFrame);
```

# Image

## Using HTML Image
```html
<img id="pineapple" src="pineapple.png">

<script>
context.drawImage($("#pineapple").get(0),50,50);
</script>
```

## Using Javascript Object
```js
let image = new Image();
image.src = "pineapple.png";
```

>[!Tip] Draw before loading
>```js
>let image = new Image();
>image.src = "pineapple.png";
>context.drawImage(image,50,50);
>```
>```mermaid
>sequenceDiagram
>	Main ->> Async: image.src="pineapple.png";
>	activate Async
>	Note left of Main: draw-image
>	Async --x Main: loaded...
>```
>This can be solved by the Load Event.
>```js
>let image = new Image();
>image.onload = function() {
>	context.drawImage(image,50,50);
>}
>image.src = "pineapple.png";
>```

## Advance `drawImage()`

```js
drawImage(
	image,
	sx, sy, sw, sh,
	dx, dy, dw, dh
);
```

>[!Tips] Disable bluring
>`context.imageSmoothingEnabled = false`

