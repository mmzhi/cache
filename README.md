## cache
cache is a Go cache manager. It can use many cache adapters. The repo is inspired by `database/sql` .


## How to install?

	go get github.com/mmzhi/cache


## What adapters are supported?

As of now this cache support memory, Memcache and Redis.


## How to use it?

First you must import it

	import (
		"github.com/astaxie/beego/cache"
	)

Then init a Cache (example with memory adapter)

	bm, err := cache.NewCache("memory", `{"interval":60}`)	

Use it like this:	
	
	bm.Put("mmzhi", 1, 10)
	bm.Get("mmzhi")
	bm.IsExist("mmzhi")
	bm.Delete("mmzhi")


## Memory adapter

Configure memory adapter like this:

	{"interval":60}

interval means the gc time. The cache will check at each time interval, whether item has expired.


## Memcache adapter

Memcache adapter use the vitess's [Memcache](http://code.google.com/p/vitess/go/memcache) client.

Configure like this:

	{"conn":"127.0.0.1:11211"}


## Redis adapter

Redis adapter use the [redigo](http://github.com/garyburd/redigo/redis) client.

Configure like this:

	{"conn":":6039"}
