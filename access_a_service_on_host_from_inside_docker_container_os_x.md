# Access a Service on Host from Inside a Docker Container OS X / mac os

On mac os, docker's *--net="host"* doesn't work.

To access a service on the host os you need to alias an unused ip to loopback.

```
sudo ifconfig lo0 alias 123.123.123.123
```

Make sure that the service on the host is listening on *0.0.0.0:port* because localhost and *127.0.0.1* wont work.

Inside the docker container, the aliased ip will then forward to 0.0.0.0 on the host.

Put this in a startup script because it will reset on reboot.

 