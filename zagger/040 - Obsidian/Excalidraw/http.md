---
created: 2023-11-15T20:54
updated: 2023-11-15T20:54
---
# http

## HTTP 请求方法:

### 理解：

- 可以这样理解，HTTP 就好比一个对象参数，里面有 Method ，代表 HTTP 的请求方法，用来告诉服务器，客户端访问你的 url 的目的是什么，是获取信息，上传数据还是删除信息。通常用到的最多就是 GET 和 POST 。
- OPTIONS 是为客户端提供一种查询 URL 地址中有哪些可用的访问方式的方法。
- PS: 留给思考，这个 OPTIONS 的使用场景是什么呢？

### POST 和 PUT 的区别：

- POST：POST的数据，服务器必须保证数据被完整的保存，并且不允许出现重复的 POST 数据提交。通常在 HTML 中通过表单来提交数据。
- PUT： PUT 允许客户端提交重复的数据，当提交重复的数据时，会用新提交的数据覆盖掉服务器已有的数据。
- PS: 这里推荐一本我读过的书籍 《图解HTTP》写的很不错，图文并茂，简单易懂，值得阅读。

### 方法Get Post

### get / post / restful 规范

## http请求的过程

### HTTP是怎么在服务端走的

- 看下面我画的一张图，这是服务器端程序、Web 服务器、客户端之间的关系

### 上图是主流的模式，Web 服务器仅起到桥梁的作用，即将浏览器的 HTTP 请求解码，转换成服务器端程序能够识别的接口调用方式，然后服务器端程序会将生成的返回封装成 HTTP Response ，并返回给用户。

- 1. 注意：在服务端，用户发的请求，如果是为了获取静态资源的话，一般是不经过服务器端程序的，直接通过服务端的缓存机制，返回资源给用户，比如 Nginx 的静态资源缓存。不走服务端程序，会大大提高响应速度。
- 2. 注意：服务端一般都是在公司的内网，外网是无法访问的，发起 HTTP 请求，其实大多数情况下都是先通过 Nginx 进行反向代理，同时也是负责流量转发，将不同的请求转发给内网特定的服务器。

## http协议 / OSI七层模型 / TCP-IP五层模型

### TCP分析 / 三次握手 / 四次握手

## DNS分析

## Header

## http状态码的意义

### 状态码

- 常用状态码

### 在 web 编程中，状态码是非常重要的事情。

### 目的：

- 是为了让开发人员和用户知道服务器是正常处理了请求还是出现了错误。了解目的，对于我们去了解状态码为什么会这样分，是非常必要的事情，至少心里不那么感觉到陌生了。

### 而在状态码中，有一个系列非常重要，那就是 3XX 系列。

- 301 ，302 的区别

	- 302 临时重定向

		- 临时重定向，意识是当服务端关闭的时候，客户端发起 url 请求，是不能成功的。它还需要向服务端发起请求，让服务端重定向到目标网址，也就是返回 location ，然后再转到目标网址。

	- PS: 思考一下，为什么会有 302 ？
	- 301 永久重定向

		- 永久重定向，是即使服务端关闭了，浏览器端发起 url 请求，也可以不经过服务端而直接转到目标网址。除非清理缓存，否则以后再次访问都是直接访问另一个地址。

- 重定向和永久重定向

	- 为了避免给网站的SEO造成不良影响，也为了给用户带来良好的访问体验，我们应该采用一些特别说明来告诉搜索引擎——“它们实际上是同一个页面”。当然，不仅仅是为了SEO，对于一个优秀的站点而言，每一个网页也都应该对应一个唯一的网址。
	- 简言之，就是当用户浏览器或搜索引擎访问某个旧的网址时，服务器告诉浏览器或搜索引擎，“该网页已经搬家了，新家的地址是……，请使用新地址来访问该网页”。
	- 永久重定向就表示该网址已经搬迁到一个永久居住的“新家”
	- 临时重定向就表示该网址搬迁到了一个临时居住的“公寓
	- [文章地址](https://blog.csdn.net/weixin_33940102/article/details/92204682)

## http头部信息

## cookie状态管理

### session / cookie / localStorage / sessionStorage

## https

## 文章集合

### [为什么XMLHTTPRequest不能跨域请求资源](https://juejin.cn/post/6999854437930008590?utm_source=gold_browser_extension)

## [文章：通过讲故事搞定前端网络知识](https://juejin.cn/post/6844903773588963342)

## 前置基础知识

### URI vs URL

- URI：Uniform Resource Identifier

	- 百度百科：在电脑术语中，统一资源标识符（Uniform Resource Identifier，URI)是一个用于标识某一互联网资源名称的字符串。 该种标识允许用户对任何（包括本地和互联网）的资源通过特定的协议进行交互操作。

- URL：uniform resource locator

	- 百度百科：统一资源定位系统（uniform resource locator;URL）是因特网的万维网服务程序上用于指定信息位置的表示方法。它最初是由蒂姆·伯纳斯·李发明用来作为万维网的地址。现在它已经被万维网联盟编制为互联网标准RFC1738。

- [文章：HTTP 协议中 URI 和 URL 有什么区别？](https://www.zhihu.com/question/21950864)

## Socket

### 概念

- Socket 在汉语中是指孔或插座的意识，顾名思义，插上了就可以通信了。Socket 一开始是作为 BSD UNIX 的进程通信机制，然后逐渐成为主流操作系统共同遵守的网络编程标准。
- Socket 是什么

	- Socket 是一个通信链的句柄，可以用来实现不同虚拟机或不同计算机之间的通信，也可以实现相同主机内的不同进程之间的通讯。

- Socket 的组成

	- Socket = IP 地址 + 端口 + 协议

### IP 地址 + 端口 + 协议 组成一个唯一标识，用来标识一个通信链路。

### 可以看到，Socket 其实是对 TCP/IP 进行了高度封装，屏蔽了很多网络细节。这样可以使开发者更好地进行网络编程。其实就是我们写个高度封装内部细节的函数，通过传参来完成指定的行为。

### 可以这么说，所有的 TCP/UDP 等编程，基本都是按照 Socket 协议标准来进行编程的，换句话说，Socket 是一套标准，就好比 DOM ，所有语言都可以按照 DOM 的接口标准来实现自己的逻辑。

### Socket 有自己的原语，开发者可以按照 Socket 的原语在不同语言下的实现方式来进行网络编程。

### WebSocket与Socket的关系

- Socket其实并不是一个协议，而是为了方便使用TCP或UDP而抽象出来的一层，是位于应用层和传输控制层之间的一组接口。
- Socket是应用层与TCP/IP协议族通信的中间软件抽象层，它是一组接口。
- 在设计模式中，Socket其实就是一个门面模式，它把复杂的TCP/IP协议族隐藏在Socket接口后面，对用户来说，一组简单的接口就是全部，让Socket去组织数据，以符合指定的协议。
- 当两台主机通信时，必须通过Socket连接，Socket则利用TCP/IP协议建立TCP连接。
- TCP连接则更依靠于底层的IP协议，IP协议的连接则依赖于链路层等更低层次。WebSocket则是一个典型的应用层协议。Socket是传输控制层协议，WebSocket是应用层协议。

### [文章：WebSocket和Socket的区别](https://www.jianshu.com/p/59b5594ffbb0/)

- 容易搞混的就是，网络中的Socket
- 通常所说的Socket API，是指操作系统中（也可能不是操作系统）提供的对于传输层（TCP/UDP）抽象的接口。
- 现行的Socket API大致都是遵循了BSD Socket规范（包括Windows）。
- 这里称规范其实不太准确，规范其实是POSIX，但BSD Unix中对于Socket的实现被广为使用，所以成为了实际的规范。
- 如果你要使用HTTP来构建服务，那么就不需要关心Socket，如果你想基于TCP/IP来构建服务，那么Socket可能就是你会接触到的API。

	- 在TCP/IP网络中HTTP的位置
	- 从上图中可以看到，HTTP是基于传输层的TCP协议的，而Socket API也是，所以只是从使用上说，可以认为Socket和HTTP类似（但一个是成文的互联网协议，一个是一直沿用的一种编程概念），是对于传输层协议的另一种直接使用，因为按照设计，网络对用户的接口都应该在应用层。

### socket图示

### 有了端口之后，我们就能定位到网络中的进程，然后进行数据通信了。但是不同的协议的数据结构不同，也就是要做不同的操作，直接操作网络传过来的数据比较复杂，这件事应该操作系统来封装一下。所以 POSIX 就定义了 socket 的标准 api，我们通过这些 api 就可以很方便的操作不同协议的数据。

### socket 的 api 分为服务端和客户端两方面：

- 服务端：bind、listen、accept、read、write、close
- 客户端：connet、write、read、close
- 图示
- POSIX 的思想是一切皆文件，所以网络通信的 socket 的 api 也设计成了 read、write 的形式。
- 服务端通过 listen 来把进程绑定到端口，客户端连接上服务端的某个端口，通过网络把数据传输到该端口，之后进行数据的读写。
- 各种语言都对 socket api 做了封装，Node.js 也不例外。
- [socket之nodejs的例子：](http://nodejs.cn/api/net.html#net_net_createconnection)

	- server代码

		- 

			- server输出

	- client代码

		- 

			- client输出

## WebSocket

### 概念

- 这是 HTML5 定义的一种新的标准协议，实现了浏览器与服务器的全双工通信。我们可以将 WebSocket 理解为 Web + Socket ，它是一种双工通信。
- WebSocket同HTTP一样也是应用层的协议，但是它是一种双向通信协议，是建立在TCP之上的。
- 什么是双工通信？

	- 就是在同一时刻，我既可以扮演通信双方的发送方，也可以扮演通信双方的接收方。

### 为什么会出现 WebSocket

- 在 WebSocket 出来之前，前端的 Web 通信基本就靠 HTTP ，但是 HTTP ( 1 或者 2 ) 请求本身有一些缺陷，比如：
- 首部信息冗余，每次发送请求，都要携带大量冗余信息。
- 不能实现双工通信。
- 所以在这个技术背景下，WebSocket 技术出现了，弥补了 HTTP 的缺陷。但是我们又不能不用 HTTP ，因为已经用的场景太多了，所以就综合了一下，让 WebSocket 协议是在 HTTP 协议之上的。这样就可以做到平稳过渡到新的通信协议上了。

### WebSocket 的通信原理

- WebSocket 是建立在 HTTP 之上的，也就意味着你要建立 WebSocket 的话，需要走一次 HTTP ，走完后，你的 WebSocket 就建立起长连接了。然后只要不是主动断开的，就会保持好客户端和服务端之间的连接，不会使其断开。当有数据传输的时候，会直接进行传输，不再发起 HTTP 请求。
- 前端使用 WebSocket 很简单，就那么几个 API ，可自行去查看。但是我们要清楚每个 API 究竟发生了什么事情，只有理解了背后的那些真相，我们才算是真正理解了 WebSocket 。

### WebSocket和http的关系

- 图示
- 首先Websocket是基于HTTP协议的，或者说借用了HTTP的协议来完成一部分握手。

	- 在握手阶段是一样的

- 看个典型的Websocket握手（借用Wikipedia的。。）

	- GET /chat HTTP/1.1
Host: server.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
Origin: http://example.com
	- 熟悉HTTP的童鞋可能发现了，这段类似HTTP协议的握手请求中，多了几个东西。

		- 1. 

			- Upgrade: websocket
			- Connection: Upgrade
			- 这个就是Websocket的核心了，告诉Apache、Nginx等服务器：注意啦，窝发起的是Websocket协议，快点帮我找到对应的助理处理~不是那个老土的HTTP。

		- 2.

			- Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==

				- 首先，Sec-WebSocket-Key 是一个Base64 encode的值，这个是浏览器随机生成的，告诉服务器：泥煤，不要忽悠窝，我要验证尼是不是真的是Websocket助理。

			- Sec-WebSocket-Protocol: chat, superchat

				- 然后，Sec_WebSocket-Protocol 是一个用户定义的字符串，用来区分同URL下，不同的服务所需要的协议。简单理解：今晚我要服务A，别搞错啦~

			- Sec-WebSocket-Version: 13

				- 最后，Sec-WebSocket-Version 是告诉服务器所使用的Websocket Draft（协议版本），在最初的时候，Websocket协议还在 Draft 阶段，各种奇奇怪怪的协议都有，而且还有很多期奇奇怪怪不同的东西，什么Firefox和Chrome用的不是一个版本之类的，当初Websocket协议太多可是一个大难题。。不过现在还好，已经定下来啦~大家都使用的一个东西~ 脱水：服务员，我要的是13岁的噢

- 服务器会返回下列东西，表示已经接受到请求， 成功建立Websocket啦！

	- HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: HSmrc0sMlYUkAGmm5OPpG2HaGWk=
Sec-WebSocket-Protocol: chat
	- 这里开始就是HTTP最后负责的区域了，告诉客户，我已经成功切换协议啦~
Upgrade: websocket
Connection: Upgrade
	- 依然是固定的，告诉客户端即将升级的是Websocket协议，而不是mozillasocket，lurnarsocket或者shitsocket。
	- 然后，Sec-WebSocket-Accept 这个则是经过服务器确认，并且加密过后的 Sec-WebSocket-Key。服务器：好啦好啦，知道啦，给你看我的ID CARD来证明行了吧。。后面的，Sec-WebSocket-Protocol 则是表示最终使用的协议。

- WebSocket 看成是 HTTP 协议为了支持长连接所打的一个大补丁，它和 HTTP 有一些共性，是为了解决 HTTP 本身无法解决的某些问题而做出的一个改良设计。
- 在以前 HTTP 协议中所谓的 keep-alive connection 是指在一次 TCP 连接中完成多个 HTTP 请求，但是对每个请求仍然要单独发 header；
- 所谓的 polling 是指从客户端（一般就是浏览器）不断主动的向服务器发 HTTP 请求查询是否有新数据。
- WebSocket 解决的第一个问题是

	- 通过第一个 HTTP request 建立了 TCP 连接之后，之后的交换数据都不需要再发 HTTP request了，使得这个长连接变成了一个真.长连接。
	- 但是不需要发送 HTTP header就能交换数据显然和原有的 HTTP 协议是有区别的，所以它需要对服务器和客户端都进行升级才能实现。
	- 在此基础上 WebSocket 还是一个双通道的连接，在同一个 TCP 连接上既可以发也可以收信息。此外还有 multiplexing 功能，几个不同的 URI 可以复用同一个 WebSocket 连接。这些都是原来的 HTTP 不能做到的。

- 技术细节

	- WebSocket 可能进入某种半死不活的状态

		- 原有网络世界的一些缺陷性设计。上面所说的 WebSocket 真.长连接虽然解决了服务器和客户端两边的问题，但坑爹的是网络应用除了服务器和客户端之外，另一个巨大的存在是中间的网络链路。一个 HTTP/WebSocket 连接往往要经过无数的路由，防火墙。你以为你的数据是在一个“连接”中发送的，实际上它要跨越千山万水，经过无数次转发，过滤，才能最终抵达终点。在这过程中，中间节点的处理方法很可能会让你意想不到。
		- 这些坑爹的中间节点可能会认为一份连接在一段时间内没有数据发送就等于失效，它们会自作主张的切断这些连接。在这种情况下，不论服务器还是客户端都不会收到任何提示，它们只会一厢情愿的以为彼此间的红线还在，徒劳地一边又一边地发送抵达不了彼岸的信息。而计算机网络协议栈的实现中又会有一层套一层的缓存，除非填满这些缓存，你的程序根本不会发现任何错误。这样，本来一个美好的 WebSocket 长连接，就可能在毫不知情的情况下进入了半死不活状态
		- WebSocket 的设计者们也早已想过。就是让服务器和客户端能够发送 Ping/Pong Frame（RFC 6455 - The WebSocket Protocol）。这种 Frame 是一种特殊的数据包，它只包含一些元数据而不需要真正的 Data Payload，可以在不影响 Application 的情况下维持住中间网络的连接状态。

- [文章:WebSocket 是什么原理？为什么可以实现持久连接？](https://www.zhihu.com/question/20215561)

### WebSocket 优点

- 支持推送功能，服务端可以向客户端推送数据。
- 减少通信量，一方面是 WebSocket 的首部信息很小，另一方面是不需要频繁进行 HTTP 连接了，可以进行持久连接。

### 这里推荐一篇文章，写的挺不错，可以看看：

- [WebSocket 是什么原理？为什么可以实现持久连接？](https://www.zhihu.com/question/20215561)

## C/S 和 B/S 架构

### 对于前端工程师来说，还是要去了解一下 web 架构的发展演变的，提到发展演变，不得不说一下 C/S 和 B/S 架构。

### C/S

- C/S ，即 Client/Server ，当前网络编程的主流架构模型。 Clent 是客户端的意识，S 是 服务端的意识。

### B/S

- 即 Browser/Server ，是使用 Web 浏览器作为客户端的应用软件。

### 从上面介绍我们可以推断出，C/S 中的 C 有很多，比如 APP ，桌面应用等。但是 B/S 中的 B 只特指浏览器。

### B/S 结构与 C/S 结构相比，有什么区别或者说有什么优势呢？

- 优点

	- 第一： 最显而易见的就是，B/S 部署升级快，无需应用程序更新，因为 B/S 系统的所有应用程序都是部署在服务器上的，不需要更新客户端软件。所以很多 APP 内都内嵌 H5 ，Hybrid 。 因为不需要审核，可以直接发布。为什么不需要审核呢，是因为前端的跨域限制，JS 是无法获取设备其他信息的，不需要担心安全问题，也就不用审核了。
	- 第二： 跨平台，因为操作系统都支持 Web 浏览器，所以只需要在浏览器中运行就好了。

- 缺点

	- 安全性要求高，B/S 架构是建立在广域网上的，面向所有用户。通过 url 就可以访问服务器端资源，所以安全性要求要比 C/S 要高。

