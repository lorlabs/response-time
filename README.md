## response-time

Response time middleware for [lor](https://github.com/sumory/lor).

This module creates a middleware that records the response time for requests in HTTP servers. The "response time" is defined here as the elapsed time from when a request enters this middleware to when the response is written out to the client.



### Install

```
git clone https://github.com/lorlabs/response-time
```

copy `response_time` to your lor project directory.


### Usage

example:

```
local lor = require("lor.index")

-- import the middleware.
local reponse_time_middleware = require("app.middleware.response_time")

local app = lor()

app:use(reponse_time_middleware({
    digits = 1,
    header = 'X-Response-Time',
    suffix = true
}))

app:get("/index", function(req, res, next)
	res:send("hello world!")
end)

app:run()
```


params:

```
{
    digits = 1, -- how many floats
    header = 'X-Response-Time', -- response header name
    suffix = true  -- add "ms" suffix or not
}
```



