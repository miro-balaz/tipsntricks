# tipsntricks
## Windows / linux / cygwin line endings
home is c:\Users\your-user-name or variable %USERPROFILE% , but sometimes it is inside directory where you installed cygwin

puto following lines into ~/.bash_profile   for cygwin to be able to run .sh files
```
export SHELLOPTS
set -o igncr
```

put this into Dockerfile, to fix line endings
```
RUN sed -i 's/\r//g' docker/docker-entrypoint.sh
```

## VS code working directory
In menu Debug/OpenConfigurations put following line into your configuration
``` "cwd": "${workspaceFolder}/src" ```

## Docker
### Do not use :latest
  It is just a default tag it is not moving tag, it is creators responsibility to make it latest
### [Use corporate proxy](https://medium.com/@saniaky/configure-docker-to-use-a-host-proxy-e88bd988c0aa)
Edit the file ```/etc/systemd/system/docker.service.d/http-proxy.conf ```

```
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:3128"
Environment="HTTPS_PROXY=http://127.0.0.1:3128"
Environment="NO_PROXY=localhost,127.0.0.1,172.17.0.1,172.30.1.1"
```

# Mongo in windows
MongoDB has problems with traditional windows shares, this is workaround
```
docker volume create --name=mongodata
docker run -d -p 27017:27017 -v mongodata:/data/db --name=mymongo mongodb:3.3
```
instead of ``` docker run -v c:\datafolder ... ```

# Docker compose post install
```mount /tmp -o remount,exec```
or cryptic message will apper *docker-compose: error while loading shared libraries: libz.so.1: failed to map segment from shared object*

# certificates and docker

It didn't helped to add just as certificate authority the self signed certificate itself (cert is .crt file)
## Linux -docker
put cert into ```/etc/docker/cetrs.d/<domain>```  domain can be with port, ot it can be ip
## Linux -CA
put cert into ```/usr/local/share/ca-certificates/``` and run ```update-ca-certificates```

## Windows
```~/.docker/certs.d```  same as linux

# Windows CA 
run mmc, add certificates plugin and choose trusted root certificate authority/all tasks/import or just google it




