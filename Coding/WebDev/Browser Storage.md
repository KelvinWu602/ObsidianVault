#webdev 

| storage method | size       | server accessibility | lifetime      |
| -------------- | ---------- | -------------------- | ------------- |
| cookies        | 1024 bytes | full                 | until expired |
| localStorage   | 5MB        | JS only              | permanent     |
| sessionStorage | 5MB        | JS only              | tab session              |

# Usage
```js
window.localStorage.setItem("key","value");
value = window.localStorage.getItem("key");
window.removeItem("key");
window.localStorage.clear();
//same for session storage
```
