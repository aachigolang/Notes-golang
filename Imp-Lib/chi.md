### chi router

https://scene-si.org/2018/03/12/handling-http-requests-with-go-chi/
https://www.alexedwards.net/blog/making-and-using-middleware


go get -u github.com/go-chi/chi


### Basic chi router
```go
r := chi.NewRouter()
r.Use(middleware.Logger)
r.Get("/", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("welcome"))
    })
```

### stampede
https://github.com/go-chi/stampede

cached := stampede.Handler(512, 1 * time.Second)

### Ratelimit
https://github.com/go-chi/httprate/blob/master/_example/main.go

```go
// Overall rate-limiter, keyed by IP and URL path (aka endpoint).
	//
	// This means each user (by IP) will receive a unique limit counter per endpoint.
	// r.Use(httprate.Limit(10, 10*time.Second, httprate.KeyByIP, httprate.KeyByEndpoint))
// Here we set a specific rate limit by ip address and userID
		r.Use(httprate.Limit(10, 10*time.Second, httprate.KeyByIP, func(r *http.Request) (string, error) {
			token := r.Context().Value("userID").(string)
			return token, nil
		}))
```
###  limits 
```go
// Stop processing after 2.5 seconds.
r.Use(middleware.Timeout(2500 * time.Millisecond))

// Only one request will be processed at a time.
		r.Use(middleware.Throttle(1))
```

### Creating your own middleware
https://github.com/alexsergivan/blog-examples/blob/master/middleware/main.go





