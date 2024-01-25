# 内容安全策略CSP
## HTTP header Content-Security-Policy
## <meta http-equiv="Content-Security-Policy" content="default-src 'self'; img-src https://*; child-src 'none';" />
## 示例
- 1 内容均来自同一个源
  - Content-Security-Policy: default-src 'self'
- 2 一个网站管理者允许内容来自信任的域名及其子域名（域名不必须与 CSP 设置所在的域名相同）
  - Content-Security-Policy: default-src 'self' *.trusted.com
- 3 一个网站管理者允许网页应用的用户在他们自己的内容中包含来自任何源的图片，但是限制音频或视频需从信任的资源提供者，所有脚本必须从特定主机服务器获取可信的代码。
  - Content-Security-Policy: default-src 'self'; img-src *; media-src media1.com media2.com; script-src userscripts.example.com

