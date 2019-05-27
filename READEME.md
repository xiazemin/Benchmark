pwd
/Users/didi/goLang/src/github.com/xiazemin/Benchmark

go test -run=BenchmarkStringJoin1 -bench=. -benchtime="3s" -cpuprofile profile_cpu.out
goos: darwin
goarch: amd64
pkg: github.com/xiazemin/Benchmark
BenchmarkStringJoin1-4   	50000000	        76.8 ns/op	      16 B/op	       1 allocs/op
PASS
ok  	github.com/xiazemin/Benchmark	4.129s


-benchtime 可以控制benchmark的运行时间
b.ReportAllocs() ，在report中包含内存分配信息，例如结果是:
BenchmarkStringJoin1-4 300000 4351 ns/op 32 B/op 2 allocs/op


-4表示4个CPU线程执行；300000表示总共执行了30万次；4531ns/op，表示每次执行耗时4531纳秒；32B/op表示每次执行分配了32字节内存；2 allocs/op表示每次执行分配了2次对象

git clone --depth=1 https://github.com/brendangregg/FlameGraph.git /Users/didi/goLang/FlameGraph
go get github.com/uber/go-torch

PATH="$PATH:/Users/didi/goLang/FlameGraph"
cd src/github.com/xiazemin/Benchmark/
 ~/goLang/bin/go-torch -b profile_cpu.out -f profile_cpu.torch.svg

