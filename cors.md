# CORS 跨源资源共享
## 简单请求
- 请求方法为 HEAD、GET、POST
- HTTP 的头信息不超出以下几种字段：
  - Accept
  - Accept-Language
  - Content-Language
  - Last-Event-ID
  - Content-Type：只限于三个值 application/x-www-form-urlencoded、multipart/form-data、text/plain
- 请求中的任意 XMLHttpRequestUpload 对象均没有注册任何事件监听器；XMLHttpRequestUpload 对象可以使用 XMLHttpRequest.upload 属性访问
- 请求中没有使用 ReadableStream 对象
- 请求中没有使用 FormData 对象
- Content-Type 的值为 application/x-www-form-urlencoded、multipart/form-data、text/plain 之一
