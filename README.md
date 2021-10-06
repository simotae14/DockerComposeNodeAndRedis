### Project using Docker Compose

We want to compose different containers, one redis server and multiple instances of a nodejs app. The purpose of this project is to count the number of visitors in the nodejs app.

## Define a docker-compose.yml file
We need to define a `docker-compose.yml` to define the different <i>services</i> that we want to connect
```yaml
version: '3'
services:
  redis-server:
    image: 'redis'
  node-app:
    build: .
    ports:
      - "4001:8081"
```

and now we can just update the `index.js` to use, inside the Redis-Client the brand new created <b>`redis-server`</b>

```javascript
const client = redis.createClient({
  host: 'redis-server',
  port: 6379
});
```

## docker-compose commands
To run our services we can just launch
`docker-compose up`
and visit the url
[localhost:4001](http://localhost:4001)