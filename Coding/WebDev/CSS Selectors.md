# Basic

```css
h1     {...} //html tag
.class {...} //class
#btn1  {...} //ID
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

