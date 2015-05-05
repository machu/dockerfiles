# machu/tdiary docker image

# How to use this image

```
docker run -v "$(pwd)/data":/usr/src/app/data --rm -p 8080:9292 machu/tdiary
``` 

Then, access it via `http://localhost:8080` in a browser.

 * user: `user`, password: `user`

To change password, run the following command and recreate a image.

```
htpasswd -d -c dot.htpasswd
```

## via docker-compose

to be written...

## how to create this image

```
docker build -t machu/tdiary .
```

# Supported Docker versions

This image is supported on Docker version 1.6.0.