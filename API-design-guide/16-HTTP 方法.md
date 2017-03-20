#HTTP 方法#

网络化API支持多种传输协议，包括HTTP。因此，每一个API方法 **必须** 遵守其映射到的特定HTTP方法的HTTP协议相关的要求。更多细节，请参考超[文本传输协议规范](https://tools.ietf.org/html/rfc2616#section-9)和它的[补丁方法](http://tools.ietf.org/html/rfc5789)RFC。

安全的方法，比如 HTTP GET(和HEAD)，除了检索以外不应该执行任何动作。 特别地， HTTP GET 应该被认为是安全的，而且不应该有任何客户端可见的副作用。 

HTTP的幂等意味着，多个相同的请求和一个请求的副作用相同。GET, PUT, 和 DELETE 都是幂等的HTTP方法。注意，幂等只针对服务器端的副作用，与任何响应无关。特别要注意的是，DELETE 不存在的资源 **应该** 返回404 (Not Found)。

 
HTTP POST 和 PATCH 方法，既不是安全的，也不是幂等的。 (PATCH 请参考[RFC 5789](https://tools.ietf.org/html/rfc5789))

| HTTP Verb                                                 | Safe | Idempotent |
| --------------------------------------------------------- | ---- | ---------- |
| [GET](https://tools.ietf.org/html/rfc2616#section-9.3)    | Yes  | Yes        |
| [PUT](https://tools.ietf.org/html/rfc2616#section-9.6)    |      | Yes        |
| [DELETE](https://tools.ietf.org/html/rfc2616#section-9.7) |      | Yes        |
| [POST](https://tools.ietf.org/html/rfc2616#section-9.5)   |      | Yes        |
| [PATCH](https://tools.ietf.org/html/rfc5789)              |      | Yes        |
