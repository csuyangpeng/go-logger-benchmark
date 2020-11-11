# go-logger-benchmark


# Benchmark
利用go testing的benchmark功能，对列出的三方库进行压力测试，利用testing的Parallel进行并发测试，分别把cpu参数设置为1，2，4进行测试。

测试脚本： https://github.com/senses2008/go-logger-benchmark

zap的性能很突出，zerolog也符合“Zero Allocation JSON Logger”的定义。

Result:
```
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Beego.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkBeegoTextFile           4100502              1415 ns/op             288 B/op          5 allocs/op
BenchmarkBeegoTextFile-2         3273606              2001 ns/op             288 B/op          5 allocs/op
BenchmarkBeegoTextFile-4         2385339              2700 ns/op             288 B/op          5 allocs/op
BenchmarkBeegoTextFile-8         1827255              3249 ns/op             288 B/op          5 allocs/op
BenchmarkBeegoTextFile-16        1692684              3519 ns/op             288 B/op          5 allocs/op
BenchmarkBeegoTextFile-20        1719895              3557 ns/op             288 B/op          5 allocs/op
PASS
ok      go-logger-benchmark     53.968s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Logrus.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkLogrusTextFile          1126089              5109 ns/op             472 B/op         14 allocs/op
BenchmarkLogrusTextFile-2         702780              7544 ns/op             472 B/op         14 allocs/op
BenchmarkLogrusTextFile-4         775260             10265 ns/op             472 B/op         14 allocs/op
BenchmarkLogrusTextFile-8         523987             10086 ns/op             472 B/op         14 allocs/op
BenchmarkLogrusTextFile-16        522571             10436 ns/op             473 B/op         14 allocs/op
BenchmarkLogrusTextFile-20        597808             10618 ns/op             473 B/op         14 allocs/op
PASS
ok      go-logger-benchmark     41.368s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Zap.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkZapTextFile            23735436               245 ns/op               2 B/op          0 allocs/op
BenchmarkZapTextFile-2          36649190               168 ns/op               2 B/op          0 allocs/op
BenchmarkZapTextFile-4          55973862               107 ns/op               2 B/op          0 allocs/op
BenchmarkZapTextFile-8          64386153                93.0 ns/op             2 B/op          0 allocs/op
BenchmarkZapTextFile-16         95781754                62.8 ns/op             2 B/op          0 allocs/op
BenchmarkZapTextFile-20         92794114                62.8 ns/op             2 B/op          0 allocs/op
PASS
ok      go-logger-benchmark     58.173s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Gologging.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkGologgingTextFile               1385840              4185 ns/op             920 B/op         17 al   locs/op
BenchmarkGologgingTextFile-2             1375696              4095 ns/op             920 B/op         17 al   locs/op
BenchmarkGologgingTextFile-4              923832              7312 ns/op             920 B/op         17 al   locs/op
BenchmarkGologgingTextFile-8              756489              7989 ns/op             920 B/op         17 al   locs/op
BenchmarkGologgingTextFile-16             760384              7999 ns/op             920 B/op         17 al   locs/op
BenchmarkGologgingTextFile-20             753658              8009 ns/op             921 B/op         17 al   locs/op
PASS
ok      go-logger-benchmark     45.474s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Zerolog.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkZerologTextFile         3064875              1959 ns/op               0 B/op          0 allocs/op
BenchmarkZerologTextFile-2       1992912              3061 ns/op               0 B/op          0 allocs/op
BenchmarkZerologTextFile-4       1538082              3822 ns/op               0 B/op          0 allocs/op
BenchmarkZerologTextFile-8       1000000              5534 ns/op               0 B/op          0 allocs/op
BenchmarkZerologTextFile-16      1000000              5797 ns/op               0 B/op          0 allocs/op
BenchmarkZerologTextFile-20      1000000              5817 ns/op               0 B/op          0 allocs/op
PASS
ok      go-logger-benchmark     44.295s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Seelog.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkSeelogTextFile          1377043              4399 ns/op             440 B/op         11 allocs/op
BenchmarkSeelogTextFile-2        1000000              6166 ns/op             440 B/op         11 allocs/op
BenchmarkSeelogTextFile-4         943298              6293 ns/op             440 B/op         11 allocs/op
BenchmarkSeelogTextFile-8         829287              6873 ns/op             440 B/op         11 allocs/op
BenchmarkSeelogTextFile-16        838896              6956 ns/op             440 B/op         11 allocs/op
BenchmarkSeelogTextFile-20        941930              6814 ns/op             440 B/op         11 allocs/op
PASS
ok      go-logger-benchmark     40.885s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Log15.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkLog15TextFile            848736              6196 ns/op             936 B/op         15 allocs/op
BenchmarkLog15TextFile-2          599578             10936 ns/op             936 B/op         15 allocs/op
BenchmarkLog15TextFile-4          523755             10573 ns/op             936 B/op         15 allocs/op
BenchmarkLog15TextFile-8          529848             11241 ns/op             936 B/op         15 allocs/op
BenchmarkLog15TextFile-16         504208             11288 ns/op             936 B/op         15 allocs/op
BenchmarkLog15TextFile-20         486783             11395 ns/op             936 B/op         15 allocs/op
PASS
ok      go-logger-benchmark     35.227s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Gokit.*Text"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkGokitTextFile           2719525              2111 ns/op              96 B/op          2 allocs/op
BenchmarkGokitTextFile-2         1857340              3085 ns/op              96 B/op          2 allocs/op
BenchmarkGokitTextFile-4         1426822              4282 ns/op              96 B/op          2 allocs/op
BenchmarkGokitTextFile-8         1000000              5640 ns/op              96 B/op          2 allocs/op
BenchmarkGokitTextFile-16         981074              5866 ns/op              96 B/op          2 allocs/op
BenchmarkGokitTextFile-20         998997              5801 ns/op              96 B/op          2 allocs/op
PASS
ok      go-logger-benchmark     44.738s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Logrus.*JSON"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkLogrusJSONFile           637386              9361 ns/op            1880 B/op         32 allocs/op
BenchmarkLogrusJSONFile-2         426361             15513 ns/op            1880 B/op         32 allocs/op
BenchmarkLogrusJSONFile-4         321414             17952 ns/op            1881 B/op         32 allocs/op
BenchmarkLogrusJSONFile-8         299770             20015 ns/op            1883 B/op         32 allocs/op
BenchmarkLogrusJSONFile-16        292106             21017 ns/op            1886 B/op         32 allocs/op
BenchmarkLogrusJSONFile-20        272778             21071 ns/op            1888 B/op         32 allocs/op
PASS
ok      go-logger-benchmark     37.332s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Zap.*JSON"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkZapJSONFile            15197043               415 ns/op             194 B/op          1 allocs/op
BenchmarkZapJSONFile-2          22546420               257 ns/op             194 B/op          1 allocs/op
BenchmarkZapJSONFile-4          39636123               144 ns/op             194 B/op          1 allocs/op
BenchmarkZapJSONFile-8          56241469               107 ns/op             195 B/op          1 allocs/op
BenchmarkZapJSONFile-16         59836892               102 ns/op             196 B/op          1 allocs/op
BenchmarkZapJSONFile-20         53809200               109 ns/op             197 B/op          1 allocs/op
PASS
ok      go-logger-benchmark     37.004s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Zerolog.*JSON"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkZerologJSONFile         2654978              2223 ns/op               0 B/op          0 allocs/op
BenchmarkZerologJSONFile-2       1894832              3280 ns/op               0 B/op          0 allocs/op
BenchmarkZerologJSONFile-4       1266662              4814 ns/op               0 B/op          0 allocs/op
BenchmarkZerologJSONFile-8        942694              6106 ns/op               0 B/op          0 allocs/op
BenchmarkZerologJSONFile-16       910641              6347 ns/op               0 B/op          0 allocs/op
BenchmarkZerologJSONFile-20       962186              6282 ns/op               0 B/op          0 allocs/op
PASS
ok      go-logger-benchmark     46.295s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Log15.*JSON"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkLog15JSONFile            570414             10999 ns/op            2096 B/op         31 allocs/op
BenchmarkLog15JSONFile-2          286490             18804 ns/op            2096 B/op         31 allocs/op
BenchmarkLog15JSONFile-4          329764             19830 ns/op            2096 B/op         31 allocs/op
BenchmarkLog15JSONFile-8          265450             21739 ns/op            2097 B/op         31 allocs/op
BenchmarkLog15JSONFile-16         257613             22557 ns/op            2097 B/op         31 allocs/op
BenchmarkLog15JSONFile-20         253131             22837 ns/op            2098 B/op         31 allocs/op
PASS
ok      go-logger-benchmark     36.808s
go test -cpu=1,2,4,8,16,20 -benchmem -benchtime=5s -bench "Gokit.*JSON"
goos: linux
goarch: amd64
pkg: go-logger-benchmark
BenchmarkGokitJSONFile           1689169              3625 ns/op             298 B/op          5 allocs/op
BenchmarkGokitJSONFile-2         1291916              4657 ns/op             298 B/op          5 allocs/op
BenchmarkGokitJSONFile-4          940161              7161 ns/op             298 B/op          5 allocs/op
BenchmarkGokitJSONFile-8          775746              6872 ns/op             299 B/op          5 allocs/op
BenchmarkGokitJSONFile-16         856984              7142 ns/op             299 B/op          5 allocs/op
BenchmarkGokitJSONFile-20         803672              7041 ns/op             299 B/op          5 allocs/op
PASS
ok      go-logger-benchmark     44.587s

```
