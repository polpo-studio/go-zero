# go-zero 魔改版

## Features | 特性

- [] go-swagger : 基于go-swagger而不是官方的@doc注解
- [] 多国语言支持
- [] 优化错误信息处理,支持多语言错误
- [] 简单易用的校验器
- [] 支持代码生成，生成API,RPC 和 web 端的CRUD代码
- [] 支持多种额外插件如GORM, RocketMQ
- [X] rpc logic group分组
- [X] rpc client enable/disable

### RPC 分组
```shell
goctls rpc protoc -I $wd "$wd/slash.proto" --go_out="$output/pb" --go-grpc_out="$output/pb" --zrpc_out="$output" --group -style=go_zero
```


```protobuf
service Greet {
    // group: foo
    rpc SayHello(HelloReq) returns (HelloResp);
    
    // group: bar
    rpc SayHi(HiReq) returns (HiResp);
    
    rpc SayHalo(SayHaloReq) returns (SayHaloResp);
}
```

### rpc client enable/disable

```go
func NewClientIfEnabled(c RpcClientConf, options ...ClientOption) Client {}
```
