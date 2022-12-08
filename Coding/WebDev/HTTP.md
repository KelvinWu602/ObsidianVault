# Structure
```http
GET / HTTP/1.1
Host: cse.hkust.edu.hk
Connection: keep-alive 
Upgrade-Insecure-Requests: 1 
User-Agent: Mozilla/5.0 ... 
Accept: text/html, ... 
Accept-Encoding: gzip, deflate, br 
Accept-Language: en-US
```

```http
HTTP/1.1 200 OK 
Date: Sat, 12 Mar 2022 16:32:17 GMT 
Server: Apache 
Cache-Control: private 
Keep-Alive: timeout=5, max=100 
Connection: Keep-Alive 
Transfer-Encoding: chunked 
Content-Type: text/html; charset=UTF-8

body
```

# Status Code

| code | meaning               |
| ---- | --------------------- |
| 200  | OK                    |
| 400  | Bad Request           |
| 404  | Not Found             |
| 500  | Internal Server Error |

# Content types
1. text/plain
2. image/png
3. image/svg+xml
4. text/javascript
5. application/json