### http请求的完全过程
##  1.1 浏览器根据域名解析ip地址（三层）
##  1.2 浏览器与web服务器建立一个tcp连接（四层）
        TCP 的三次握手
##  1.3 浏览器给web服务器发送一个http请求（应用层，本文主要说明）
 请求报文：一个http请求报文由请求行（request line）、请求头部（headers）、空行（blank line）、请求数据（request body）4部分组成
 
# 1.3.1 请求行
    请求行分为三个部分：

##  request：
    包括
    - headers
    - body
## response
    包括
    - headers
    - body

##  get   
    查询资源
