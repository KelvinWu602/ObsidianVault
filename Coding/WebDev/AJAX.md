#webdev 

# Purpose

For the small data updates in Single Page Application to minimise waiting time.

# Request

## HTTP Get

Client side
```js
fetch("https://static.data.gov.hk/covid-vaccinesummary.json")
.then(response=>response.json()) //or .text() if the response is text, here return the JS object.
.then(data=>{
	...
})
.catch(err=>{alert(err)});
```

## HTTP Post

Client side
```js
fetch("getuser",
	{
		method: "POST",
		headers: {"Content-Type": "application/json"},
		body: JSON.stringify(json) 
	})
.then(data=>{..}).then(json=>{..}).catch(err=>{..})
```

Server side
```js
app.use(express.json());

app.post("/getuser", (req,res)=>{
	const data = req.body; //return json object
	res.json(data); //put json object in the ()
})
```
