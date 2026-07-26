# PJWT-Protos

passport jwt 解析服务 grpc proto 包

新版 `GenToken` 调用方应提供与签发者绑定的 `issue_key` 和 `issuer`。迁移期间
服务端仍可接受不包含这两个字段的旧请求；`valid` 的单位为纳秒，服务端会限制
最大有效期。`ParseJwt` 不需要签发凭据，解析结果会通过 `claims.issuer` 返回 JWT
的签发者。

新版 Go gRPC 代码要求服务端实现按值嵌入 `UnimplementedPassportServer`，不要嵌入
`*UnimplementedPassportServer`；后者为 nil 时会在注册服务期间触发 panic。

```shell
go get -u github.com/ncuhome/PJWT-Protos
```

proto 更新重新生成命令:

```shell
protoc --go_out=. --go_opt=paths=source_relative \
  --go-grpc_out=. --go-grpc_opt=paths=source_relative ./jwt.proto
```
