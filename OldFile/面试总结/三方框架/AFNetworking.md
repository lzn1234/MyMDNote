## AFNetworking

- 网络通信模块(AFURLSessionManager、AFHTTPSessionManger)
- 网络状态监听模块(Reachability)
- 网络通信安全策略模块(AFSecurityPolicy)
- 网络通信信息序列化/反序列化模块(Serialization)
- 对于iOS UIKit库的扩展(UIKit)

核心模块是网络通信模块AFURLSessionManager，AFNetworking基于NSUrlSession进行封装的，AFURLSessionManager是围绕NSUrlSesstion进行封装的，其他模块都是为了配合网络通信



AFNetworking 是对NSURLSessionTask的封装。AFHTTPSessionManager继承AFURLSessionManager对网络请求进行管理，使用AFURLRequestSerialization对网络请求进行封装，使用AFURLResponseSerialization对响应体进行处理，使用AFSecurityPolicy对服务器证书进行校验。支持HTTPS协议，支持本地证书和服务器证书进行对比验证。AFN数据传递主要使用block和notifacation方式。



请求过程

- GET/POST方法调用抽象的请求方法，指明请求参数，调用全能数据请求方法，指明数据请求方式和参数。
- 对请求进行序列化，如果序列化失败，就执行failure block。
- 为每一个NSURLSessionDataTask的dataTask增加代理。
- 对每一个NSURLSessionDataTask的dataTask增加代理的具体实现，对dataTask设置请求之后的回调delegate和处理block

