nats.go

Usefull code for Nats server
```go
//connect to nats server
nc, err := nats.Connect(nats.DefaultURL)
//connect to servers cluster
servers := []string{"nats://127.0.0.1:1222", "nats://127.0.0.1:1223", "nats://127.0.0.1:1224"}
nc, err := nats.Connect(strings.Join(servers, ","))
// connecting and giving name for nats server for better understanding
nc, err := nats.Connect("demo.nats.io", nats.Name("API Name Option Example"))
nc, err := nats.Connect("demo.nats.io", nats.Name("API Options Example"), nats.Timeout(10*time.Second))

nc, err := nats.Connect("demo.nats.io", nats.Name("API NoEcho Example"), nats.NoEcho())
nats.NoReconnect()
nats.MaxReconnects(10)

//Avoiding the Thundering Herd
nats.DontRandomize()
//Pausing Between Reconnect Attempts
nats.ReconnectWait(10*time.Second)
//Buffering Messages During Reconnect Attempts
nats.ReconnectBufSize(5*1024*1024)
//Listening for Reconnect Events
nc, err := nats.Connect("demo.nats.io",
    nats.DisconnectErrHandler(func(nc *nats.Conn, err error) {
        // handle disconnect error event
    }),
    nats.ReconnectHandler(func(nc *nats.Conn) {
        // handle reconnect event
    }))

```