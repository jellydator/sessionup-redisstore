# sessionup-redisstore

[![Build status](https://travis-ci.org/jellydator/sessionup-redisstore.svg?branch=master)](https://travis-ci.org/jellydator/sessionup-redisstore)
[![GoDoc](https://godoc.org/github.com/jellydator/sessionup-redisstore?status.png)](https://godoc.org/github.com/jellydator/sessionup-redisstore)

Redis session store implementation for [sessionup](https://github.com/jellydator/sessionup)

## Installation
```
go get github.com/jellydator/sessionup-redisstore
```

## Usage
Create and activate a new RedisStore:
```go
// create redigo connection pool
pool := &redis.Pool{
    Dial: func() (redis.Conn, error) {
         return redis.Dial("tcp", "localhost:6379")
    },
}

store, err := redisstore.New(pool, "customers")
if err != nil {
      // handle error
}

manager := sessionup.NewManager(store)
```
