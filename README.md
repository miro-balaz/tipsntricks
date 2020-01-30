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
