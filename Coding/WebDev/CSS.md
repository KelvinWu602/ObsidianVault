2 kinds of css:
1. element's css properties
2. external css file

Linking to External Style Sheets
```html
<link href="style.css" rel="stylesheet">
```

You can use style sheet to avoid repetition. See CSS Selectors on how to select elements.
 
# CSS Properties

Each element has it's own css properties.

```html
<h1 style="color: red; font-family: Arial"> Hey </h1>
```


## Font

| property    | meaning     | examples         |
| ----------- | ----------- | ---------------- |
| font-family | font style  | Helvetica, Arial |
| font-size   |             | 18px             |
| font-weight | stroke size | bold             |

```html
<p style="font-family: 'Times New Roman'; font-size:32px;font-weight:bold"> Hey </p>
```
<p style="font-family: 'Times New Roman'; font-size:32px;font-weight:bold"> Hey </p>

## Paragraph 

| property    | meaning              | examples                  |
| ----------- | -------------------- | ------------------------- |
| text-align  | horizontal alignment | left,right,center,justify |
| line-height |                      | 40px                      |

```html
<p style="background:white;color:black;text-align:center;line-height:70px"> hey </p>
```
<p style="background:white;color:black;text-align:center;line-height:70px"> hey </p>

## Color

| property         | meaning          | examples  |
| ---------------- | ---------------- | --------- |
| background-color |                  | lightgray |
| background       | background-color | blue      |
| color            | text color       | red       |

```html
<p style="background:white;color:blue"> Hey </p>
```
<p style="background:white;color:blue"> Hey </p>

[Color codes here.](https://htmlcolorcodes.com/color-names/)

## Span

```html
<p> This is a <span style="background:white;color:red"> span </span>. </p>
```
<p> This is a <span style="background:white;color:red"> span </span>. </p>




# Inline and Block

## Inline elements

Those will not open a new line:
- span
- b

Example:
<p style="background:black"> In the middle of paragraph, we see a <span> span </span> and <b> bold text </b> . </p>

## Block elements

Those will occupy a rectangular area, start on a new line.
- h1
- div

### Spacing

![[Pasted image 20221204121935.png]]
- Element: width, height
- Padding
- Border
- Margin

Box (width:200px, height:40px)
<div style="background:black;margin:0px;padding:0px;width:200px;height:40px">Text in Box</div>

Box (width:200px, height:40px, margin:20px)
<div style="background:black;margin:20px;padding:0px;width:200px;height:40px">Text in Box</div>

Box (width:200px, height:40px, margin:20px, padding:10px)
<div style="background:black;margin:20px;padding:10px;width:200px;height:40px">Text in Box</div>

Box (width:200px, height:40px, margin:20px, border: 2px solid red)
<div style="background:black;margin:20px;padding:0px;width:200px;height:40px;border: 2px solid red">Text in Box</div>

Box (width:200px, height:40px, margin:20px, border: 2px solid red, border-radius:10px)
<div style="background:black;margin:20px;padding:0px;width:200px;height:40px;border: 2px solid red;border-radius:10px">Text in Box</div>

