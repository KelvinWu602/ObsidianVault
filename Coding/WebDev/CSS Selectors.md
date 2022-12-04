# Basic
Selection could be based on:
- HTML Tag
- Class
- ID

## Tag 

Select all h1
```css
h1 {...}
```

## Class

Select all apple class members
```css
.apple {...}
```

## ID

Select btn1
```css
#btn1 {...}
```


# Advanced

## Multiple Selection
Using comma to choose multiple elements
```css
h1, b {...} //Choose all h1 and b
```

# Hierarchy Selection
Using space to denote belongship.
```css
ul b {...} //Choose all b under ul
```

>[!Tips] Immediate children
>Note that this does not requires immediate belongship!

Above will choose the below b tab.
```html
<ul>
	<li> Text <b>tt</b></li>
	<li> Text <b>tt</b></li>
</ul>
```

## Immediate Children
Using > to denote immediate belongship.
```css
ul > b {...}
```

