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
### Using with Vagrant
If you wish to have Vagrant automatically add the proxy to any started VMs if the polipo container is running

Install the `vagrant-proxyconf` plugin:

    vagrant plugin install vagrant-proxyconf

Add the `Vagrantfile` from the vagrant directory in this repo to `~/.vagrant.d`, this will automatically detect the docker-machines ip and check that Polipo is running before attempting to have Vagrant use the proxy.

If a valid proxy is detected you will see the following on vagrant up:

    Using Polipo Proxy: http://192.168.99.100:8123 
