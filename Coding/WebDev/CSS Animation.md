#webdev 

# Keyframes Rule

First, declare the rule
```css
@keyframes move {
	from {left:0px}
	to   {left:50px}
}
```

Then, apply the rule
```html
<h1 style="position:relative; animation:move 2s">Bouncing</h1>
```

>[!Tips] position:relative
>Position must be relative such that the `left` css property is effective. 

Since the animation is non-repetitive and does not remain at the ending frame, after 2 seconds, it will return to it's initial position.

>[!Note] Remains at the ending frame
>`animation-fill-mode: forwards`

>[!Note] Animation Timing
>`animation-timing-function: linear`

>[!Tips] Animation iteration
>`animation-iteration-count: 5`


## Transform Property

```css
@keyframes move {
	from {transform: translateX(0px);}
	to   {transform: translateX(200px);}
}
```

Other tranformation:
1. translate(x,y)
2. rotate(angle)
3. scale(x,y)


# Animation Event
JQuery#Other Events|JQuery Event

```js
$(".number").on("animationend",()=>{
	$(".number").text("Animation ended!");
});
```

| event                | triggered                       |
| -------------------- | ------------------------------- |
| `animationstart`     | when animation starts           |
| `animationiteration` | when one iteration is completed |
| `animationend`       | when animation finishes         |


## Restart Animation

```js
$(".emt").on("animationend", ()=>{
	$(".ent").css("animation-name","name_here")
});
```
