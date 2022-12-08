This is a subtopic of the HTML.

# Form Headers

|         headers          |        usuage        | example                                                                                      |
|:------------------------:|:--------------------:|:-------------------------------------------------------------------------------------------- |
|          input           |      text input      | `<input type="text" name="id">`                                                              |
|          input           |      file input      | `<input type="file" name="file" enctype="multipart/form-data">`                               |
|          input           |        submit        | `<input type="submit">`                                                                      |
|          input           |    password input    | `<input type="password" name="password" maxlength="12">`                                     |
|          input           |       checkbox       | `<input type="checkbox" name="important">`                                                   |
|          input           |       radio MC       | `<input type="radio" name="set" value="value">`                                              |
|          input           |     email input      | `<input type="email" name="email">`                                                          |
|          input           |      url input       | `<input type="url" name="website">`                                                          |
|          input           |     number input     | `<input type="number" name="age" value="15" min="0" max="100" step="1">`                     |
|          input           |        slider        | `<input type="range" name="height" min="0" max="200" step="5">`                              |
|          input           |         date         | `<input type="date" name="exam-date">`                                                       |
|          input           |         time         | `<input type="time" name="exam-time">`                                                       |
|          input           |     color picker     | `<input type="color" name="favourite">`                                                      |
|          input           |    required input    | `<input type="text" required placeholder="haha">`                                            |
| select, optgroup, option |    selection list    | `<select name="role"> <optgroup label="group"> <option>value</option> </optgroup> </select>` |
|         textarea         | multiline text input | `<textarea name="message"> Default text </textarea>`                                         |

# Posting Data

## HTTP Get Request

```html
<form method="GET" action="/endpoint">
	...
</form>
```

When the form is submitted, it will send information via the query string
`.../endpoint?name1=value1&name2=value2`

## HTTP Post Request

```html
<form method="post" action="/endpoint">
	...
</form>
```

When the form is submitted, it will send information via the http post request.
``` http
POST /endpoint HTTP/1.1
...
Content-Length: 29
Content-Type:application/x-www-form-urlencoded
...

firstname=Gibson&lastname=Lam
```

At server side, we can get post data by
```js
app.use(express.urlencoded({extended:true}));

app.post("/endpoint", (req,res)=>{
	const {firstname,lastname} = req.body;
	...
})
```

### File Uploads

The file will be uploaded in chunks
```http
POST /endpoint HTTP/1.1
...
Content-Type: multipart/form-data;boundary=Boundary-1234567890

--Boundary-1234567890
Content-Type: image/png
Content-Disposition: form-data;filename="me.png";name="myimage"

bytes here
next block
```

At server side,
install `multer`
```js
const multer = require("multer");
const uplaod = multer({dest:"uploads/"}); //folder for temp file

app.post("/upload", upload.single("name"), (req,res)=>{
	fs.copyFile(req.file.path, "public/"+req.file.originalname);
	fs.unlink(req.file.path); //delete temp file
});
```

`req.file`
| attribute    | example        |
| ------------ | -------------- |
| fieldname    | 'name'         |
| originalname | 'origin.png'   |
| encoding     | '7bit'         |
| mimitype     | 'image/png'    |
| destination  | 'uploads/'     |
| filename     | hash           |
| path         | 'uploads/hash' |
| size         | num of bytes   |

