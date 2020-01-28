# tipsntricks
## Windows /linux/ cygwin line endings
home is c:\Users\<name> or variable %USERPROFILE%

puto following lines into ~/.bash_profile   for cygwin to be able to run .sh files
```
export SHELLOPTS
set -o igncr
```

put this into Dockerfile, to fix line endings
```
RUN sed -i 's/\r//g' docker/docker-entrypoint.sh
```
