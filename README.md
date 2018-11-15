# Speedometer

> A go-http-routing benchmark fork from [go-http-routing-benchmark](https://github.com/julienschmidt/go-http-routing-benchmark)

这是一个用来测试 go web 框架性能的基准测试（~~跑分软件~~）。

原本想用已有的测试代码 `go-http-routing-benchmark` 来进行测试，但是其已经许久没有更新，而且也无法正常运行。所以就仿照它写了这个 Speedometer ，一来可以正常运行，二来也可以按自己喜好添加新的 web 框架进去进行测试和更改测试项目。

## 使用方法

### 安装

```shell
$ go get -u github.com/Zophyr/Speedometer
```

> ⚠️ 该步骤可能会需要较多的时间，请耐心等待。

### 运行

1.进入 Speedometer 文件

```shell
$ cd $GOPATH/src/github.com/Zophyr/Speedometer
```

2.执行 Speedometer 测试

**测试所有 router**

```shell
$ go test -bench=.
```

**测试部分 router**

> eg. Martini & Gin & GorillaMux

```shell
$ go test -bench="Martini|Gin|GorillaMux"
```

## 测试结果

***Gin vs GorillaMux***

```shell
go test -bench="GorillaMux|Gin"
```

结果：

```shell
#GithubAPI Routes: 203
   Gin: 52064 Bytes
   GorillaMux: 1329248 Bytes

#GPlusAPI Routes: 13
   Gin: 3936 Bytes
   GorillaMux: 66544 Bytes

#ParseAPI Routes: 26
   Gin: 6912 Bytes
   GorillaMux: 106632 Bytes

#Static Routes: 157
   Gin: 30480 Bytes
   GorillaMux: 591136 Bytes

goos: darwin
goarch: amd64
pkg: github.com/Zophyr/Speedometer
BenchmarkGin_Param               	20000000	        65.3 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_Param        	  500000	      3135 ns/op	    1280 B/op	      10 allocs/op
BenchmarkGin_Param5              	20000000	       120 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_Param5       	  300000	      4793 ns/op	    1344 B/op	      10 allocs/op
BenchmarkGin_Param20             	 5000000	       304 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_Param20      	  200000	     10554 ns/op	    3452 B/op	      12 allocs/op
BenchmarkGin_ParamWrite          	10000000	       153 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_ParamWrite   	  500000	      3363 ns/op	    1280 B/op	      10 allocs/op
BenchmarkGin_GithubStatic        	20000000	        93.2 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GithubStatic 	  100000	     17749 ns/op	     976 B/op	       9 allocs/op
BenchmarkGin_GithubParam         	10000000	       161 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GithubParam  	  200000	     10595 ns/op	    1296 B/op	      10 allocs/op
BenchmarkGin_GithubAll           	   50000	     29143 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GithubAll    	     300	   5387694 ns/op	  251648 B/op	    1994 allocs/op
BenchmarkGin_GPlusStatic         	20000000	        66.4 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GPlusStatic  	 1000000	      2345 ns/op	     976 B/op	       9 allocs/op
BenchmarkGin_GPlusParam          	20000000	        87.5 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GPlusParam   	  300000	      4127 ns/op	    1280 B/op	      10 allocs/op
BenchmarkGin_GPlus2Params        	20000000	       116 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GPlus2Params 	  200000	      7711 ns/op	    1296 B/op	      10 allocs/op
BenchmarkGin_GPlusAll            	 1000000	      1248 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_GPlusAll     	   20000	     65454 ns/op	   16112 B/op	     128 allocs/op
BenchmarkGin_ParseStatic         	20000000	        72.6 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_ParseStatic  	  300000	      3825 ns/op	     976 B/op	       9 allocs/op
BenchmarkGin_ParseParam          	20000000	        76.3 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_ParseParam   	  500000	      3729 ns/op	    1280 B/op	      10 allocs/op
BenchmarkGin_Parse2Params        	20000000	        91.3 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_Parse2Params 	  500000	      3946 ns/op	    1296 B/op	      10 allocs/op
BenchmarkGin_ParseAll            	 1000000	      2134 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_ParseAll     	   10000	    127993 ns/op	   30288 B/op	     250 allocs/op
BenchmarkGin_StaticAll           	  100000	     19305 ns/op	       0 B/op	       0 allocs/op
BenchmarkGorillaMux_StaticAll    	    1000	   1645517 ns/op	  153328 B/op	    1421 allocs/op
PASS
ok  	github.com/Zophyr/Speedometer	59.501s
```