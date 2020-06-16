https://pkg.go.dev/github.com/go-redis/redis?tab=doc

https://kb.objectrocket.com/redis/how-to-use-redis-go-client-go-redis-redis-with-golang-592
https://www.alexedwards.net/blog/working-with-redis

### setting up redis with docker


docker run --name some-redis -d redis


go-redis/redis
Redis client for Golang supporting Redis Sentinel and Redis Cluster out of the box.	


github.com/go-redis/redis/v7

### Connecting to redis

	client := redis.NewClient(&redis.Options{
		Addr:     "localhost:6379",
		Password: "", // no password set
		DB:       0,  // use default DB
	})



err := client.Set("key", "value", 0).Err()
val, err := client.Get("key").Result()


