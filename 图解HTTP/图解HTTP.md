# 图解HTTP
## 第一章 了解WEB及网络的基础
> - 使用Http协议访问Web
![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-1skjd1fu-1650373647623)(img.png)\]](https://img-blog.csdnimg.cn/def2ee5d55974acfa592bf8591354fe4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> -  Http的诞生
> - http诞生于需要知识共享，伴随着http诞生之后，浏览器随之火爆，微软与网景浏览器争斗最终以微软胜利告终。http在1996年5月版本正式任命为http/1.0。
    > http是在TCP/IP基础之上起作用的。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-mdQT3XXv-1650373647624)(img_2.png)\]](https://img-blog.csdnimg.cn/0a4758bc2e3a4c1093b2f04439349c99.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 与http密不可分的三个协议:IP、TCP和DNS、
> - 负责传输的IP协议：ip（internet protocol）网际层协议，把各种数据包传送给对方，中间会涉及到跨网段传输，用到ARP技术，奖逻辑网络地址转化昵称mac地址。
> - 确保可靠性传输的TCP协议：TCP位于传输层，提供可靠的字节流服务，TCP协议会通过三次握手建立连接。
> - 负责域名解析的DNS服务：DNS将域名转换成IP地址。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-6VKf8P6u-1650373647624)(img_3.png)\]](https://img-blog.csdnimg.cn/d29471671e9d483caff11eed5fa4a91d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_16,color_FFFFFF,t_70,g_se,x_16)

> - URL：统一资源定位符，URI：统一资源标识。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-KSfskrCv-1650373647625)(img_4.png)\]](https://img-blog.csdnimg.cn/89f77fa893ef4fefb4acd191c82631f7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
## 第二章 简单的HTTP协议
> - HTTP是不保存状态的协议，为了实现保存状态功能于是引入了Cookie技术。
> - method方法：get：获取资源，post：传输实体主主体，put：传输文件，head：获取报文首部，用于确认URI的有效性以及资源的更新日期时间等，delete：删除文件，put和
    > delete不带验证机制，所以一般也不会使用delete方法，options：询问支持方法，trace：追踪路径，让web服务器将之前的请求通信环回给客户端的方法，容易引发站点追踪，不常用。
    > connect：要求用隧道协议连接代理，connect方法要求在于代理服务器通信时建立隧道，实现用是隧道协议进行TCP通信。主要用SSL和RLS协议把通信内容加密后经网络隧道传输。
> - http1.0和http1.1所支持的方法
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-beqbjXAI-1650373647625)(img_5.png)\]](https://img-blog.csdnimg.cn/71ff6362ea45410bb576c63e94858c27.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 非持久连接：在http1.0中默认是非持久化连接的，但是可以设置为持久连接。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-zbRLxe1o-1650373647626)(img_6.png)\]](https://img-blog.csdnimg.cn/652716d535674148a3ce945365ac6b17.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 持久连接：在http1.1中默认是持久化连接的。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-U8mYrmAl-1650373647626)(img_7.png)\]](https://img-blog.csdnimg.cn/75209320f36a46c49b32574f7aff3856.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 管线化：持久化连接的存在使得管线化存在了可能，不用等待响应就可以直接发送下一个请求。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-ofgtb0qM-1650373647626)(img_8.png)\]](https://img-blog.csdnimg.cn/9d3208e019cc4ae38fef77e005b11949.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - Cookie进行状态管理：cookie技术通过请求和响应报文中写入cookie信息来控制客户端的状态。1，cookie会根据从服务器发送的响应报文内的叫做Set-Cookie的首部字段信息，通知
    > 客户端保存cookie,2，当下次客户端在往服务器发送请求时候，客户端会主动在请求报文中添加cookie值后发送,3，服务器接收到客户端发来的cookie之后，会查询究竟是哪个客户端发来的
    > 连接请求。
## 第三章 HTTP报文内的HTTP信息
> - HTTP报文是由多行（CR+LF作换行符）数据构成的字符串文本，HTTP报文可以分为报文首部和报文主体两部分，两者起初是由（CR+LF）划分的，通常并不一定有报文主体。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-9199LNw1-1650373647627)(img_9.png)\]](https://img-blog.csdnimg.cn/5167a41584d04844a6190adb752225ee.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-JjApCX6m-1650373647628)(img_15.png)\]](https://img-blog.csdnimg.cn/535116dd9d1248ccbb426c93d8117518.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-HJZJ9ECJ-1650373647629)(img_16.png)\]](https://img-blog.csdnimg.cn/b9594ee03bf84268a7e77b9fc1b67494.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-pkjZCZYc-1650373647630)(img_17.png)\]](https://img-blog.csdnimg.cn/65003aacedf043ffbcdd52e0029b1840.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 请求报文和响应报文
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-JHuuisJ8-1650373647630)(img_10.png)\]](https://img-blog.csdnimg.cn/434c9046704a41f19d69ca3964052a9d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-LnG1U58k-1650373647631)(img_11.png)\]](https://img-blog.csdnimg.cn/50173132fb974baa9dcc10a98a961a85.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 报文中的参数解释：请求行：包含请求方法、请求URI和HTTP版本。状态行：响应状态码、原因短语和HTTP版本。首部字段：一般由通信首部、请求首部、响应首部和实体首部。
> - 编码提升传输速率：类似于发送邮件中内增加附件时，为了使邮件变小，会使用ZIP压缩文件之后在进行传输。HTTP协议中存在内容编码也有类似大的功能，进行实体内容编码，
    > 客服端负责解码，常用的内容编码：gzip（GNU zip）、compress（UNIX系统中的标准压缩）、deflate（zlib）、identity（不进行编码）。分割发送的分块传输编码：
    > 把实体主体分块的功能称为分块传输编码，分块传输编码分为多个块，每个块都会用十六进制来标记块的大小，最后一个块会用“0（CR+LF）”来标记。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-XbuYnqKt-1650373647632)(img_12.png)\]](https://img-blog.csdnimg.cn/93f6c786a213462ea8bb43d88a96f1de.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 发送多种数据的多部分对象集合：类似于邮件传输的MIME（Multipurpose Internet Mail Extemsions）功能，Http也采用了多部分对象集合，发送一个报文时候可以含有
    > 多个类型实体，通常是图片或者文件上传时候使用：multipart/form-data用于web表单上传文件使用、multipart/byteranges状态码206响应报文包含多个范围内容时候使用、
    > multipart/form-data、multipart/by，在使用字符串来分割实体之前要插入“--”标记进行分割。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-26xbXTjU-1650373647632)(img_13.png)\]](https://img-blog.csdnimg.cn/df04348837b645428f9711c7d48ac1bc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 获取部分内容的请求范围：可以获取资源的部分内容，适用于断开之后从接受了资源处开始继续请求资源，指定范围请求，Range Request，range可以支持多重参数。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-EwLmCmh7-1650373647633)(img_14.png)\]](https://img-blog.csdnimg.cn/88290f15458947db8e15d75a3d965389.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 内容协商（Content Negotiation）：返回最合适的内容，涉及到浏览器默认语言、字符集、编码等设置，请求服务器的会返回最适合的内容：Accept、Accept-Charset、
    > Accept-Encoding、Accept-Language、Content-Language。内容协商技术：服务器驱动协商：由服务器进行内容协商、客户端驱动协商：由客户端进行内容协商的方式，手动选择、
    > 透明协商：由服务器和客户端驱动的结合体，
## 第四章 返回结构的HTTP状态码
> - 状态码告知了服务端返回的请求结果，状态码的类别：
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-zvv9POY5-1650373647633)(img_18.png)\]](https://img-blog.csdnimg.cn/dab77c25edc64525b2735d86354973db.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 2XX：200（正常返回）、204（No Content，请求得到正常处理，返回的响应报文不含实体的主体部分，浏览器页面不发生更新）、206（Partial Content该状态码表示
    > 对客户端进行了范围请求）
> - 3XX：301（Move Permanently永久性重定向）
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-e7J2Ug5j-1650373647634)(img_19.png)\]](https://img-blog.csdnimg.cn/c68f31c42f784a3b82426e2c68f55569.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> 302（Found临时性重定向，该状态码请求的资源已被分配了新的URI，希望本用户本次能使用新的URI访问），302（See Other该状态码请求对应的资源存在另一个URI，应该使用
> get的方法获得资源）
![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-fn3jVcrx-1650373647636)(img_20.png)\]](https://img-blog.csdnimg.cn/146bb083d8ae4b4ca569cc3022d5c7c9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> 304（Not Modified表示客户端发送附带条件的请求时，服务器允许访问资源，但为满足条件）、307（Temporary Redirect临时重定向）
> - 4XX：客户端出现了问题，400（Bad Request表示请求报文存在语法错误）、401（Unauthorized，表示发送的请求需要通过HTTP认证（BASIC认证、DIGEST认证）的认证信息）
    > 403（Forbidden，服务器拒绝访问请求）、404（Not Found服务器没有请求的资源）
> - 5XX：500（Internal Server Error服务器未知的错误）、503（Service Unavailable表明服务器暂处于超载负荷或者正在停机维修）
## 第五章 与HTTP协作的Web服务器
> - 代理：具有转发功能的应用程序，有缓存代理（可以将资源的副本缓存在代理服务器上面）和透明代理（不对报文做任何的加工）
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-g6WadT2I-1650373647637)(img_21.png)\]](https://img-blog.csdnimg.cn/cf40828f4e05410a881bbca9666f1a63.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 网关：网关是转发其他服务器通信数据的服务器，利用网关可以由HTTP请求转换成其他协议通信，利用网关可以提高通信的安全，因为可以在客服端和网关通信链路上面加密以确保连接
    > 的安全。比如网关可以连接数据库使用sql语句查询。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-YeLd6CRn-1650373647638)(img_22.png)\]](https://img-blog.csdnimg.cn/abebb4fed43e4799a8fae8c08ebbcdf0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 隧道：隧道可按要求建立起一条与其他服务器的通信线路，届时使用SSL等加密手段进行通信。隧道的目的是确保客户端与服务器进行安全通信
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-mK6GeCVP-1650373647638)(img_23.png)\]](https://img-blog.csdnimg.cn/b44d9dadd8c2432384348d0bc1c3a8bc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - 确保资源的缓存：缓存服务器，客户端会直接获取缓存服务器上面的数据，客户端缓存：存储在浏览器本地。
## 第六章 HTTP首部
> - 在HTTP协议通信交互中使用的首部字段，不限于RFC2616中定义的47中首部字段，还有Cookie、setCookie和Content-Disposition德国在其它RFC中定义的首部字段。
    ![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-UF8IN8gA-1650373647639)(img_24.png)\]](https://img-blog.csdnimg.cn/6cd3864d500c45f7bd41019f3d449ba5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-vQ2TuXmA-1650373647640)(img_25.png)\]](https://img-blog.csdnimg.cn/642cac2d9d3d45f082aa27ef37c46ccc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-pJB2yCY6-1650373647640)(img_26.png)\]](https://img-blog.csdnimg.cn/dcad9fea1423479cbef1f3cc8ed76946.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-7O6w7DBH-1650373647641)(img_27.png)\]](https://img-blog.csdnimg.cn/5c6ac5e7674a4ac5a9babf87a2763c67.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-YFM3QMH6-1650373647642)(img_28.png)\]](https://img-blog.csdnimg.cn/aae51a0c29bf425cbd1518a7fa0b06f8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)

> - HTTP首部字段将定义成缓存代理（End-to-end Header）和非缓存代理(Hop-by-hop Header)的行为


## 第七章 确保Web安全的HTTPS
> - HTTP不足：明文传输、不验证通信方的身份（可能会遭到伪装）、无法证明报文的完整性（可能会被篡改）
> - 通信加密，HTTP协议中没有加密机制，但是可以通过SSL（Secure Socket Layer，安全套接字层）或TLS（Transport Layer Security，安全层传输协议）的组合使用，加密HTTP的通信内容。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/bbca4f69b9d34ca4bbffcb7c6086164e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 内容加密：将HTTP报文里所含的内容进行加密进行传输。
> - HTTP带来的问题：任何人都可以发起请求，会知道客户端和服务器无法真正的确定对方，有可能是被伪装的。
> - 查明对手的证书，证书由第三方机构颁发，用来证明服务器和客户端实际存在的，通过证书可以证明服务器，客户端持有证书也可以完成个人身份的确认。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/3d70b2c90ed34d7badf5e21dae477098.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 无法证明报文的完整性，可能已经被篡改，虽然使用HTTP协议有确定报文的完整性算法的方法，但事实上并不便捷可靠。其中常用的是MD5和SHA-1等散列值校验方法，以及用确认文件的数字签名方法。
> - HTTPS=HTTP+加密+认证+完整性保护，使用https，https是身披ssl外壳的http
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/bc60db0a0e2643e39e580fc2545b9536.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 相互交换密匙的公开密匙加密技术，SSL采用的是公开密匙加密的加密处理方式。共享密匙加密的困境，客户端和服务器端共享密匙，容易被攻击者窃取。使用非对称加密，采用公开密匙加密数据，接收者用私匙进行解密接收。
> - HTTPS采用混合加密的方式，在交换密匙的过程中采用公开加密（就是非对称加密），之后建立连接之后使用共享密匙加密（对称加密）。非对称加密效率比对称加密的效率低。
> - 证明公开密钥正确性的证书，因为客户端无法确定公开密钥是否正确，顾存在CA机构（Certificate Authority）。
> - 具体流程：服务器会向CA机构申请公开密钥，CA机构会判定申请者身份，对已申请的公开密钥做数字签名，并将该公开密钥放入公钥证书里面。客户端请求服务器的时候，服务器会将证书方法客户端，客户端拿到证书之后会到CA机构做认证，认证之后采用公钥进行加密传输数据。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/7ff70c3456f0451394f8e5b7abcb9302.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
## 第八章 确认访问用户身份的认证
> - HTTP使用的认证方式：BASIC认证（基本认证）、DIGEST（摘要认证）、SSL客户端认证、FormBase认证（基于表单认证）。
> - 基于表单的认证：涉及到session管理以及cookie的应用。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/695fd21486104d4a93ab4d201e15b452.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
## 第九章 基于HTTP的功能追加协议
> - HTTP的瓶颈：因为HTTP请求必须由客服端发起，由服务器响应并返回给客户端，一个连接智能发送一个请求，并且是整体性的请求，多次访问的时候会存在冗余的首部，无法关注变化的部分。
> - Ajax的解决方案：（Asynchronous JavaScript and XML）可以达到局部的web页面替换加载的一部通信手段。
> - Comet的解决方法：一旦服务器发生变化了，Comet不会让请求等待，而是直接给服务端响应返回，这是一种通过低延迟应答，模拟实现服务器向客户端推送的功能。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/23596cf629904237b4046b2bbdb5e6c1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - SPDY的设计与功能：多路复用流、赋予请求优先级、压缩HTTP首部、推送功能、服务器提示功能。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/c30cdf9c21a94424be4a19ca4d2e1661.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 使用浏览器进行全双工通信的WebSocket：推送功能、减少通信量（一直保持连接状态，减少连接的开销）。为了实现webcoket，需要使用HTTP中的Upgrade首部字段，告知服务器通信协议发生改变，已达握手的目的。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/7cc9553d8d5941088ce9a3a3347511b9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - HTTP/2.0
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/f19917fb6b7441c7b856dcf3c65e83d4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
## 第十章 构建Web内容的技术
> - 因JAVA而普及的Servlet，Servlet是一种能在服务器上创建动态内容的程序，是java语言实现的一个接口。
> - XML（eXtensible Markup Language）可扩展标记语言、
> - javascript衍生的轻量级易用的json（javascript object Notation）
## 第十一章 Web攻击技术
![在这里插入图片描述](https://img-blog.csdnimg.cn/145f3d5b67ae4af782b9ff310b0297a0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5bCP6ZmI5ZCM5a2m54ix5a2m5Lmg,size_20,color_FFFFFF,t_70,g_se,x_16)
> - 针对Web引用的攻击模式：主动攻击（SQL注入，OS注入）和被动攻击。
> - XSS（Cross-Site Scripting跨站脚本攻击）：利用虚假输入表单骗取用户的个人信息，利用脚本窃取用户的cookie值，在被害者不知情的情况下帮助攻击者发送恶意请求，或者显示伪造文章或图片。