- 标签： `HTTP`, `TCP`
- 时间： `2018-03-08`
- 更新： ``

## Q: 谈谈你对 TCP 的理解
Q: TCP 是在哪个OSI 的哪个层!通讯过程是全双工还是半双工(单工)?
- `传输层`, 
- `全双工`

* 补充说明：*
- OSI: `开放式系统互联` (`Open System Interconnection`) OSI的7层从上到下分别是 7 `应用层` 6 `表示层` 5 `会话层` 4 `传输层` 3 `网络层` 2 `数据链路层` 1 `物理层` ；其中高层（即7、6、5、4层）定义了应用程序的功能，下面3层（即3、2、1层）主要面向通过网络的端到端的数据流。

Q: `TCP` 的通讯的过程是怎么样的!
- 整个过程是`三次握手`, `四次挥手`..（具体巴拉巴拉）

## Q: `HTTP` 和 `HTTPS` 有何差异?
- `HTTP` 相对于 `HTTPS` 来说,速度较快且开销较小(没有 SSL/TSL) 对接,默认是 `80` 端口;
- `HTTP` 容易遭受域名劫持,而 `HTTPS` 相对来说就较为安全但开销较大(数据以加密的形式传递),默认 `443` 端口；
- `HTTP` 是明文跑在 TCP 上.而 `HTTPS` 跑在SSL/TLS应用层之下,TCP上的;

## Q: `HTTPS` 中的 `TLS/SSL` 是如何保护数据的
一般有两种形式,非对称加密,生成公钥和私钥,私钥丢服务器,公钥每次请求去比对验证;
更严谨的采用 CA(Certificate Authority),给密钥签名....

## Q: 介绍下 `SPDY`
谷歌推行一种协议(HTTP 之下SSL之上[TCP]),可以算是HTTP2的前身,有这么些优点
- 压缩数据(HEADER)
- 多路复用
- 优先级(可以给请求设置优先级)
而这些优点基本 HTTP2也继承下来了..

## Q: 你对 HTTP 的状态吗了解多少
* `1XX`: 一般用来判断协议更换或者确认服务端收到请求这些
  - `100`: 服务端收到部分请求,若是没有拒绝的情况下可以继续传递后续内容
  - `101`: 客户端请求变换协议,服务端收到确认

* `2xx`: 请求成功,是否创建链接,请求是否接受,是否有内容这些
  - `200`: 请求成功
  - `201`: 请求创建成功和资源创建成功

* - `3XX`: 一般用来判断重定向和缓存
  - `301`: 所有请求已经转移到新的 url(永久重定向),会被缓存
  - `302`: 临时重定向,不会被缓存
  - `304`: 本地资源暂未改动,优先使用本地的(根据If-Modified-Since or If-Match去比对服务器的资源,缓存)

* `4XX`: 一般用来确认授权信息,请求是否出错,页面是否丢失
  - `400`: 请求出错
  - `401`: 未授权,不能读取某些资源
  - `403`: 阻止访问,一般也是权限问题
  - `404`: 页面丢失,资源没找到
  - `408`: 请求超时
  - `415`: 媒介类型不被支持，服务器不会接受请求。

* `5XX`: 基本都是服务端的错误
  - `500`: 服务端错误
  - `502`: 网关错误
  - `504`: 网关超时
