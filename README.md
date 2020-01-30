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
