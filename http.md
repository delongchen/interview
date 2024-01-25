# http
## 常用状态码
### 1xx 信息 通常不会出现
### 2xx 成功
- 200 OK
- 204 No Content
## http 缓存
### expires
- 优先级高于 last-modified
- 优先级低于 etag
- 优先级低于 cache-control
### last-modified
- 优先级低于 etag
- 优先级低于 cache-control
- 优先级高于 expires
### etag
- 优先级高于 last-modified
- 优先级高于 expires
- 优先级高于 cache-control
### cache-control
#### 示例
- 禁止缓存
  - cache-control: no-cache
- 缓存静态资源
  - cache-control: max-age=31536000
#### 常用值
- max-age
  - 优先级高于 expires
  - 优先级低于 last-modified
  - 优先级低于 etag
- no-cache 与 no-store
  - no-cache: 会向服务器发送请求，但是不会使用缓存
  - no-store: 不会向服务器发送请求，也不会使用缓存
- public 与 private
  - public: 可以被任何中间人缓存
  - private: 只能被终端用户缓存
- must-revalidate 与 proxy-revalidate
  - must-revalidate: 如果缓存过期，必须向服务器发送请求，如果服务器返回 304，可以使用缓存
  - proxy-revalidate: 如果缓存过期，必须向服务器发送请求，如果服务器返回 304，可以使用缓存
