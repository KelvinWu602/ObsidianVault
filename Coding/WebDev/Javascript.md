#webdev 

# Timers
There are two important functions in javascript.
1. `setTimeout()`
2. `clearTimeout()`

You can use it to create regular call of function:
```js
let callback = ()=>{
	console.log("called");
	setTimeout(callback,5000);
};
//regularly call callback for every 5 seconds
let timer = setTimeout(callback,5000);
//stop the loop after 20 seconds
setTimeout(()=>{clearTimeout(timer)},200000);
```

Or using `setInterval`
```js
let callback = ()=>{console.log("called");}
let timer = setInterval(callback,5000); 
setTimeout(()=>{clearInterval(timer)},200000);
```

