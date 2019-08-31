## HTTP协议格式：

#### HTTP请求格式：

##### 1.首行：4.方法GET(获取)/POST(发送)/PUT/DELETE...

- url
- 版本号 HTTP/1.1  HTTP/2.0  HTTP/3.0

> 三个部分之间用空格分隔

##### 2.协议头（header）

> 若干个键值对，每个键值对占一行，每个键和值之间使用 : 分隔

##### 3.空行

> 表示header到这里就结束了

##### 4.协议正文（body）

>  一般GET请求没有body，post请求才有

------

#### HTTP响应格式：

##### 1.首行：

- 版本号
- 状态码
- 状态码描述信息

##### 2.协议头（header）

> 每个键值对占一行，每个键和值之间用  :  分隔

##### 3.空行

> header部分结束标记

##### 4.协议正文（body）

> 响应中的正文格式可以有多种.html/css/JS/图片数据/json数据



### 常见问题：

#### 1.常用的方法有哪些？

> GET,POST,PUT,DELETE,HEAD,OPTION....

#### 2.GET和POST的区别？

> GET请求往往把自定制的数据放在query_string中
>
> POST请求往往把自定制数据放在body中

- 误区1：GET是获取数据，POST是发送数据；不严谨，在如今GET也能往服务器上放数据，POST也能冲服务器上获得数据
- 误区2：GET对自定制数据的长度有限制，因为HTTP对URL的长度是有限制的；不准确，在如今URL的数据大小也能达到几十K,几百K，现在的浏览器与服务器对URL长度几乎没限制

#### 3.常见的状态码

- 200 OK 表示访问成功
- 302 Found  表示重定向
- 404 Not Found  没找到指定资源
- 403 Forbidden  没有权限
- 502 Bad Gateway 服务器出错
- 504 Gateway Timeout 服务器响应超时

> 2xx访问成功，3xx重定向，4xx客户端出错，5xx服务器出错

#### 4.常见的header有哪些？

- Content-Type：描述了body的数据格式类型
- Content-Length：描述了body的数据长度
- Host：描述了访问的主机名（IP地址/域名）
- User-Agent：声明用户的操作系统和浏览器的版本信息
- Referer：当前页面是从哪个页面跳转来的
- Cookie：字符串，浏览器的本地存储能力之一
  - Cookie中经常会包含一种叫做“身份标识”的信息session id
  - session：服务器端维护的一个数据结构，记录了用户的身份信息，session id 就是session对象的唯一身份标识，session id 保存在浏览器中，浏览器后续再访问服务器的时候，就会自动带着session id ,从而让服务器知道当前请求是哪个用户发来的
  - 服务器端使用一个HashTable之类的结构来维护若干个用户的身份信息，key就是session id ，value 就是完整的session对象
  - Cookie是按照Host这个header来划分的
