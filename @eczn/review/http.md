
# URL

https://domain.com/path/to/a.html?query=123#hash=喵

# 协议过程

客户端请求、服务端响应。

基于 TCP 实现。 

# header 

# etag

实体标签。 

比如 请求 a.html 的时候，服务器返回一个 etag （这个etag是 a.html 的哈希）, 客户端保存之。 

下一次请求 a.html 的时候，把上次的 etag 发回去，服务端做判断，如果 a.html 算的哈希没变则返回 304 否则 200，并吧 a.html 回传 

> HTTP 中并没有指定如何生成 ETag，哈希是比较理想的选择。

# Cache-Control

缓存控制, 做数据接口的时候经常用：no-cache 

还有 max-age 

禁用缓存：Cache-Control: no-cache, no-store, must-revalidate



# Cookie

Cookie 随浏览器发送，每次都会发送。 

Cookie 不能太大。 

服务端可以通过 Set-Cookie 字段来设置 Cookie 

# User-Agent

User Agent中文名为用户代理，是Http协议中的一部分，属于头域的组成部分，User Agent也简称UA。它是一个特殊字符串头，是一种向访问网站提供你所使用的浏览器类型及版本、操作系统及版本、浏览器内核、等信息的标识。通过这个标识，用户所访问的网站可以显示不同的排版从而为用户提供更好的体验或者进行信息统计；例如用手机访问谷歌和电脑访问是不一样的，这些是谷歌根据访问者的UA来判断的。

UA可以进行伪装。

# Content-Type

MIME 类型，如: text/html, application/json 

# CORS 跨域

## 服务端 

设置 Access-Control-Allow-Origin 即可 

Access-Control-Allow-* 还有好几个，比如 headers 和 methods 可以设置允许的字段或者方法 

jsonp 服务端 

## 客户端 

1. 开发环境下，做本地代理 ProxyTable、或浏览器插件禁用浏览器的 CORS 服务、jsonp
2. 线上：反向代理、jsonp


# method 

## GET 

访问网页用的，最常用。

传参用 url query 

无 body 

## POST 

有 body

传参可以用 query, 也可以用 body 

## PUT / DELETE / UPDATE / FETCH 

基本与 POST 一致，但带有了语义，用于设计 RESTful 风格的接口

# 状态码

200: ok 
301: 代表永久性转移 (Permanently Moved)
302: 代表暂时性转移 (Temporarily Moved)
304: Not Modified 
404: Not Found 
500: Inner Falut 
502: Bad Gateway 

## 来谈一下 200 和 304 吧 

## 来谈一下 301 和 302 吧 

301和302都是重定向，得谈一下重定向。 

再来谈谈区别，301永久的话，浏览器会产生强缓存，即便你改过了接口，但是浏览器有缓存就不会请求你了。 

只有在你提供的服务将要永久的搬迁的时候，采用 301 

## 来谈一下 502 吧 

Bad Gateway 网关问题，通常是 nginx 这样的服务器的错误引起的。

# http 有几次挥手和握手？TLS的中文名？TLS在哪一网络层？

3 次握手
firefox > nginx    [SYN]           在么
nginx > firefox    [SYN, ACK]      在
firefox > nginx    [ACK]           知道了


4 次挥手
firefox > nginx    [FIN]           我要关闭连接了
nginx > firefox    [ACK]           知道了, 等我发完包先
nginx > firefox    [FIN]           我发完了, 下了
firefox > nginx    [ACK]           好的, 知道了

注： 
SYN: synchronization(同步)
ACK: acknowledgement(确认:告知已收到)
FIN: finish(结束)

--- 

TLS：安全传输层协议，看得出是传输层的。。 

蛋疼。。 

# https: TLS / SSL 

架设在 SSL / TLS 上的 http 叫做 https 

网络分层。 

其实就是 SSL / TLS 的原理。 

其功能： 

1. 认证用户和服务器，确保数据发送到正确的客户机和服务器
2. 加密数据以防止被窃取
3. 数据完整性，确保不会被篡改 

CA 给服务器颁布证书，上面有服务器的公钥。 

客户端访问的时候，得到证书，利用上面的公钥加密一段数据 hello 发给服务器。 因为服务器有私钥，所以能解并发回给客户端，从而确保了服务器不是伪造的。

利用这个可以协商接下来的秘钥，利用整个钥匙做对称加密，防止被窃听。 

得益于，公钥密码体制。 


