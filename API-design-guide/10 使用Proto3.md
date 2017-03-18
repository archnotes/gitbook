# Protocol Buffers v3

本章将讨论在设计 API 时如何使用 Protocol Buffers。为了简化开发者体验并提高运行效率，gRPC API **应该**使用 Protocol Buffers v3（proto3）进行API定义。

[Protocol Buffers](https://github.com/google/protobuf) 是一种简单的语言中立并且平台中立的接口定义语言（IDL），用于定义数据结构模式和编程接口。它支持二进制和文本传输格式，并且在不同平台上使用不同的传输协议。

Proto3 是 Protocol Buffers 的最新版本，包括以下更改：

* 存在字段，也称为 ```hasField```，不适用于基本类型字段。未设置的基本泪ing字段具有语言特定的默认值。
    * 消息存在字段仍然可用，其可以使用编译器生成的 ```hasField``` 方法来测试，或者和 null 比较，或由实现定义的标记值。
* 用户定义的默认值不再可用。
* 枚举（Enum）定义**必须**从零开始。
* 必填（Required fields）字段不再可用。
* 扩展（Extensions）不再可用。改用 ```google.protobuf.Any``` 代替。
    * 由于向后和运行时兼容性原因，```google/protobuf/descriptor.proto``` 作为这一规则的例外。
* 组（Group）语法已删除。

删除这些功能的原因是使 API 设计更简单，更稳定，更高效。例如，通常需要在记录消息之前过滤一些字段，例如删除敏感信息，如果字段是必需的，则不可能执行删除操作。

有关详细信息，请参阅协议[Protocol Buffers详细文档](https://developers.google.com/protocol-buffers/)。


