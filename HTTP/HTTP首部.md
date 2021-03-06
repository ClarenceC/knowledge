## HTTP 首部

在 HTTP 报文首部中包含着平时在客户端和服务器处理至关重要的信息，下面我们一起整理一下。

还记得 [HTTP报文](./HTTP报文.md) 里面由下面两部分组成:
1. **报文首部** 报文主要为客户端和服务器分别处理请求和禹应提供所需要的信息。

2. **报文主体** 一般为用户和资源的信息都在这边。

而**报文首部** 分为两部分:
1. **请求报文首部** 由 HTTP方法，URI、HTTP版本、HTTP首部字段等组成。

2. **响应报文首部** 由 HTTP版本、状态码(数字和原因短语)、HTTP首部字段3部分构成。

### HTTP首部字段

首部字段是为了给浏览器或服务器提供报文主体大小、所使用的语言、认证信息等内容。
HTTP 首部字段结构分为 `首部字段名` : `字段值`像下面

```js
Content-Type: text/html
Keep-Alive: timeout=15, max=100 // 可以存在多值
```

### HTTP首部字段按用途分为4种类型

#### 通用首部字段(General Header Fields)
请求报文和响应报文都会使用的首部。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Cache-Control  |  控制缓存的行为  |
| Connection    |  逐步首部、连接的管理      |
| Date   | 创建报文的日期时间      |
| Pragma  | 报文指令 |
| Trailer  | 报文末端的首部一临览 |
| Transfer-Encoding  | 指定报文主体的传输编码方式 |
| Upgrade  | 升级为其他协议 |
| Via  | 代理服务器的相关信息 |
| Warning  | 错误通知 |

#### 请求首部字段(Request Header Fields)

从客户端浏览器向服务端发送请求报文时使用的首部。补充了请求的附加内容、客户端信息、响应内容相关优先级等信息。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Accept  |  用户代理可处理的媒体类型  |
| Accept-Charset  |  优先的字符集  |
| Accept-Encoding  |  优先的内容编码  |
| Accept-Language  |  优先的语言(自然语言)  |
| Authorization  |  Web认证信息  |
| Expect  |  期待服务器的特定行为  |
| From  |  用户的电子邮箱地址  |
| Host  |  请求资源所在的服务器  |
| If-Match  |  比较实体标记(ETag)  |
| If-Modified-Since  |  比较资源的更新时间  |
| If-None-Match  |  比较实体标记(与If-Match相反)  |
| If-Range  |  资源未更新时发送实体Byte的范围请求  |
| If-Unmodified-Since  |  比较资源的更新时间(与If-Modified-Since相反)  |
| Max-Forwards  | 最大传输逐跳数 |
| Proxy-Authorization  | 代理服务器要求客户端的认证信息 |
| Range | 实体的字节范围请求 |
| Referer | 对请求中 URI 的原始获取方 |
| TE | 传输编码的优先级 |
| User-Agent | HTTP 客户端程序的信息 |
| Cookie | 服务器接收到的Cookie信息 |

#### 响应首部字段(Response Header Fields)

从服务器端向客户端返回响应报文时使用的首部，补充了响应的附加内容，也会要求客户端附加额外的内容信息。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Accept-Ranges  |  是否接受字节范围请求  |
| Age  |  推算资源创建经过时间  |
| ETag  |  资源的匹配信息  |
| Locations  |  令客户端重定向至指定 URI  |
| Proxy-Authenticate | 代理服务器对客户端的认证信息 |
| Retry-After | 对再次发起请求的时机要求  |
| Server | HTTP服务器的安装信息 |
| Vary | 代理服务器缓存的管理信息 |
| WWW-Authenticate | 服务器对客户端的认证信息 |
| Set-Cookie | 开始状态管理所使用的Cookie信息 |

#### 实体首部字段(Response Header Fields)

针对请求报文和响应报文的实体部分使用的首部。补充了资源内容更新时间等与实体有关的信息。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Allow | 资源可以支持的HTTP方法 |
| Content-Encoding | 实体主体适用的编码方式 |
| Content-Language | 实体主体的自然语言 |
| Content-Length | 实体主体的大小(单位: 字节) |
| Content-Location | 替代对应资源的URI |
| Content-MD5 | 实体主体的报文摘要 |
| Content-Range | 实体主体的报文范围 |
| Content-Type | 实体主体的媒体类型 |
| Expires | 实体主体的过期时间 |
| Last-Modified | 资源最后修改日期时间 |


#### 其它首部字段

HTTP 首部字段是可以自行扩展的，所以在 Web 服务器和浏览器的应用上也会出现各种非标准的首部字段。

- **X-Frame-Options**

首部字段 X-Frame-Options 属于 HTTP 响应首部，用于控制网站内容在其他 Web 网站 Frame 标签内显示的问题。主要是为了防止点击却持攻击。

- **X-XSS-Protection**

属于 HTTP 响应首部，它是针对跨站脚本攻击(XSS)的一种对策，用于控制浏览器 XSS 防护机制的开关。

- **DNT**

属于 HTTP 请求首部，DNT(Do Not Track) 意思为拒绝个人信息被收集。表示拒绝被精准广告追踪的一种方法。

- **P3P**

属于 HTTP 响应首部，通过 P3P技术可以让 Web 网站上的个人隐私变成一种仅供程序可理解的形式，以达到保护用户隐私的目的。

上面是 HTTP/1.1 首部字段为主， 还有些不是 HTTP/1.1 添加的首部字段，`Cookies`、`Set-Cookie`、`Content-Disposition`等。


#### Fetch Metadata Request Headers

Fetch Metadata Request Headers 是 W3C 2020 的一个新提案，主要是为了避免简单 CSRF(Cross-site request forgery）跨站请求伪造等恶意攻击, 可以在元素上面定义一组 `Fetch` 请求头，以便服务器可以直接根据这些请求头信息就可以快速判断是否为其提供服务，这判断可以在反向代理或 CDNS 上面就作出响应，不需要到后端服务器上。暂时浏览器只有 Chrome 实现了。



主要有几个请求头:

- **Sec-Fetch-Dect**

表示 HTTP 请求头向服务器公开请求的目的地，是一个结构化的标记。`Sec-Fetch-Dect` 的值可以是 `audio`, `audioworklet`, `document`, `embed`, `empty`, `font`, `image`, `manifest`, `object`, `paintworklet`, `report`, `script`, `serviceworker`, `sharedworker`, `style`, `track`, `video`, `worker`, `xslt`, 和 `nested-document` 等。如果该值为无效值，服务器就应该忽略它了。

- **Sec-Fetch-Mode**

表示请求的模式, 主要有 `cors`、 `navigate`、 `nested-navigate`、 `no-cors` 等等，是用来判断这个请求是什么模式。类似 `fetch` 中的 mode.

- **Sec-Fetch-Site**

表示请求头的源和目标之间的关系是怎样的，例如跨源还是同源等关系，可以填写值有 `cross-site`、`same-origin`、`same-site`、`none` 等

- **Sec-Fetch-User**

是一个 boolean 值，表示 HTTP 请求头是否由用户激活发起，只有在是浏览器自然发起请求而且有互动的时候才会是 `true`，否则为 `false` 服务器会根据这个来判断请求是否合法。像如果点击 `form` 表单送出的时候且由 document 送出请求和使用者有互动的时候 `Set-Fetch-User` 会是 `?T` 值。

例子:

```js
Sec-Fetch-Dest: image
Sec-Fetch-Mode: no-cors
Sec-Fetch-Site: cross-site
```

```js
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
```



在一个报文请求在端对端或代理间作用的首部又可以分为两类：

1. 逐跳首部(Hop-by-hop Header)
在此类型中的首部只对单次转发有效，会因通过缓存或代理而不再转发，如果需要使用逐跳首部需要提供 `Connection` 字段，逐跳首部包括下面字段：
- Connection
- Keep-Alive
- Proxy-Authenticate
- Proxy-Authorization
- Trailer
- TE
- Transfer-Encoding
- Upgrade

除了上面这些其它都是端到端首部字段。


2. 端到端首部(End-to-end Header)

在此类中的首部会转发给请求/响应对应的最终接收目标，且必须保存在由缓存生成的响应中，另外规定它必须再被转发。


### 参考引用

- [Fetch Metadata Request Headers](https://www.w3.org/TR/fetch-metadata/)

- 图解HTTP