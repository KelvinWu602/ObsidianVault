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
>animation-fill-mode: forwards


