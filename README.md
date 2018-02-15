# **NGINX** docker container as a **Reverse-Proxy**

## 1. Clone this repo:

`$ git clone https://github.com/cbelda/nginx4reverse-proxy.git`

## 2. Edit the nginx configuration file to fit your needs
That means, edit `nginx.conf` to redirect one local URL (local for the container) to a different one. It could also be a different local one.

For example:
- nginx container running in `http://localhost:80`
- Container's URL (local) : `http://localhost:80/api`
- Proxied URL : `http://www.github.com`

nginx.conf:
```nginx
server {
    ...
    location /api {
        proxy_pass http://www.github.com;
    }
    ...
}
```

## 3. Build the image:

```
$ cd nginx4reverse-proxy
$ docker build -t nginx4reverse-proxy .
```

## 4. Run the Docker container:

```
$ docker run -it -d -p 80:80 --name=nginx4reverse-proxy nginx4reverse-proxy
```
