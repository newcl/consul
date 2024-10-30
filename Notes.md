1. bootstrap server
go run main.go agent -data-dir=tmp/consul -dev -bootstrap 

2. join 2nd server
go run main.go agent -data-dir=tmp/consul2 -dev -server-port 9300 -serf-lan-port 9301 -serf-wan-port 9302 -dns-port 9600 -http-port=9500 -grpc-port=9502 -grpc-tls-port=9503                   ✭v1.20.0-learn 

go run main.go join localhost:9302

3. start 1st client agent


go run main.go agent -data-dir=tmp/consul4 -node=myclient -client=0.0.0.0 -server-port 10300 -serf-lan-port 10301 -serf-wan-port 10302 -dns-port 10600 -http-port=10500 -grpc-port=10502 -grpc-tls-port=10503

liang@liang-win11 ~/git_projects/consul$ go run main.go join localhost:10301