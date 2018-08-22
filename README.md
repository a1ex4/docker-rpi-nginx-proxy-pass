# Nginx Proxy Pass
This docker image is an adaptation of [mikesplain/nginx-proxy-pass](https://github.com/mikesplain/nginx-proxy-pass-docker) to allow it to run out of the box on a armhf architecture, tested on a Raspberry 3.


A simple container that proxy passes to an external source.

A number of great containers for reverse proxying to containers exist(I'm a fan of jwilder/nginx-proxy) however I couldn't find any that would proxy pass to external sources on the fly.

Simply run:

```
docker run -d -p 80:80 -e TARGET_SERVER=<proxy location> a1ex4/rpi-nginx-proxy-pass
```

For example, want to proxy everything to google? WHY NOT?!

```
docker run -d -p 80:80 -e TARGET_SERVER=google.com a1ex4/rpi-nginx-proxy-pass
```

Or maybe another server on your network:

```
docker run -d -p 80:80 -e TARGET_SERVER=192.168.8.15:8080 a1ex4/rpi-nginx-proxy-pass
```

### docker compose
```
version: '2'

services:
  proxy_pass:
   image: a1ex4/rpi-nginx-proxy-pass
   container_name: proxy_pass
   ports:
    - "1000:80"
   environment:
    - TARGET_SERVER=192.168.1.254
```
