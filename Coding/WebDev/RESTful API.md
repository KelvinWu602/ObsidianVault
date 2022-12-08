#webdev 

> A HTTP based interface for server-application interactions.

Same endpoint, different method, different operations!
| Operation | HTTP method | Success     | Bad input       | Invalid ID    |
| --------- | ----------- | ----------- | --------------- | ------------- |
| Read      | GET         | 200 OK      | 400 Bad Request | 404 Not Found |
| Create    | POST        | 201 Created | 400 Bad Request | 404 Not Found |
| Update    | PUT         | 200 OK      | 400 Bad Request | 404 Not Found |
| Delete    | DELETE      | 200 OK      | 400 Bad Request | 404 Not Found | 

Server : `res.sendStatus(statusCode);`
Browser :
```js
fetch("/books")
.then(res=>{
	if(res.status==200) return res.json();
	else alert("failed");
}).then(json=>{...}).catch(err=>{...})
```

# URL interface

Format: `protocol://host/resource/id[/more resources]`
Examples:
1. http://books.com/book/2, get book id=2 
2. http://mystudents.edu/majors/cse/students/, get all students of cse major


# Express implementation
```js
app.get("/books", (req, res)=>{
	//return all books
})
app.get("/books/:bookId", (req, res)=>{
	const bookId = req.params.bookId;
	//return books[bookId]
})
app.post("/books",(req, res)=>{
	const book = req.body;
	//create new book
})
app.put("/books/:bookId", (res,req)=>{
	const bookId = req.params.bookId;
	const book = req.body;
	//books[bookId] = book
})
app.delete("/books/:bookId",(res,req)=>{
	const bookId = req.params.bookId;
	//delete books[bookId]
})
```

