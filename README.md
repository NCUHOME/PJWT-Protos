# PJWTC-Protos

passport jwt 解析服务 grpc proto 包

```shell
export GOPRIVATE=github.com/ncuhome
go get -u github.com/ncuhome/PJWT-Protos
```

proto 更新重新生成命令:

```shell
protoc --go_out=. --go-grpc_out=. ./jwt.proto
```