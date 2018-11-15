# Speedometer

> A go-http-routing benchmark fork from [go-http-routing-benchmark](https://github.com/julienschmidt/go-http-routing-benchmark)

## 使用方法

### 安装

```shell
$ go get -u https://github.com/Zophyr/Speedometer
```

### 运行

1. 进入 Speedometer 文件

```shell
$ cd $GOPATH/src/github.com/Zophyr/Speedometer
```

2. 执行 Speedometer 测试

**测试所有 router**

```shell
$ go test -bench=.
```

**测试部分 router**

> eg. Martini & Gin & Mux

```shell
$ go test -bench="Martini|Gin|Mux"
```