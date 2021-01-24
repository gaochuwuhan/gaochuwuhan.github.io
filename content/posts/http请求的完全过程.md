---
title: "Http请求的完全过程"
date: 2021-01-24T18:57:42+08:00
draft: false
---
### http请求的完全过程
##  1.1 浏览器根据域名解析ip地址（三层）
##  1.2 浏览器与web服务器建立一个tcp连接（四层）
        TCP 的三次握手
##  1.3 浏览器给web服务器发送一个http请求（应用层，本文主要说明）
 请求报文：一个http请求报文由4部分组成：
 -  请求行（request line）：发送请求命令，一旦建立了tcp连接，web浏览器就会向服务器发送请求命令，例如
GET/sample/hello.jsp HTTP1.1
 -  请求头部（request header）：浏览器发送命令之后还要以头信息的形式向web server发一些比的信息，例如
```
Accept: image/avif,image/webp,image/apng,image/*,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
Cache-Control: no-cache
Connection: keep-alive
Cookie: csrftoken=JwbbDzbfK1x0nIr3ZyzfVbfilsuuzI7r2Jay6sMCVD1TnhvlBHqvNSOpEOssePkH
Host: 127.0.0.1:1313
Pragma: no-cache
Referer: http://127.0.0.1:1313/posts/exam/
sec-ch-ua: "Google Chrome";v="87", " Not;A Brand";v="99", "Chromium";v="87"
sec-ch-ua-mobile: ?0
Sec-Fetch-Dest: image
Sec-Fetch-Mode: no-cors
Sec-Fetch-Site: same-origin
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36
```
-   空行（blank line）:当headers发送之后，还要发送一空白行告诉服务器，他已经结束了该头消息的发送
- 请求数据（request body）


 ![image](/http报文.png)


 
# 1.3.1 请求行
    请求行分为三个部分：
-   1.请求方法

**get**: 申请获取资源，而不对服务器产生任何其他影响。从网页上点击链接或地址栏输入地址来浏览网页都是get请求，请求的参数和对应的值附加在url后面，用一个问号‘？’代表url的结尾与**请求参数（body）**的开始，但传递参数长度受限制。例如/index.jsp?id=100&op=bind  ,各个数据用&隔开。这种方式不适合传送私密数据。另外由于浏览器地址字符的限制，如果需要大量传送数据的时候，不适合用get方式。

**post**: 客户端想服务器提交数据的方法。会影响服务器，可能新建资源也可能更新现有资源。允许客户端给服务器信息较多。也是将请求参数放到body中，各数据之间用&符号分开。以key：value的形式出现，可以传送大量谁，post请求对传送的数据大小没有限制，不会显示在url中。post方法多用于页面表单中，因为post也能完成get的功能

**put**: 上传某个资源

**delete**：删除某个资源

**options**： 

-   2.URL
![image](/url.png)

-   3.http协议版本： 1.0/1.1/2.0

##  1.4 服务器相应请求

http响应报文由：状态行，响应headers、空行、响应数据（response body）4部分组成
![image](/response.png)

#   1.4.1 状态行
主要知道状态码

#   1.4.2 response header

#   1.4.3  response body
e.g.
```
{
    "task_id": "58b1220a-b89e-4117-ad7e-22fe204dcd09",
    "time": "2021-01-11T06:21:23.170000+00:00",
    "tasktype": "dvrscan",
    "state": "failed",
    "devices": null
}
```
##  1.5 浏览器解析html代码，并请求html代码中的资源
    遇到静态资源时，想服务器端去请求下载

## 1.6  关闭tcp链接，浏览器对页面进行渲染给用户
    浏览器用自己内部工作机制，把请求到的静态资源和html代码进行渲染，呈现给用户。
