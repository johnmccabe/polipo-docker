[![](https://badge.imagelayers.io/johnmccabe/polipo:latest.svg)](https://imagelayers.io/?images=johnmccabe/polipo:latest 'Get your own badge on imagelayers.io')
# polipo docker image
Alpine based docker image for the polipo caching http proxy.

Contains polipo binary built from https://github.com/jech/polipo/tree/master.

Get started quickly by mapping the cache volume to your local filesystem (make sure you've created the directory first) and setting a static port mapping.

```
docker run --name polipo -v ~/.polipo-cache:/cache -d -p 8123:8123 johnmccabe/polipo
```
The proxy will now be available for use.
```
export http_proxy=http://<docker ip>:8123
```
You can also access the polipo web interface to configure/monitor the running instance, refer to the [Polipo documentation](http://www.pps.univ-paris-diderot.fr/~jch/software/polipo/manual/Web-interface.html) for more details.
```
http://<docker ip>:8123/polipo/
```
