# Troubleshooting steps

### Port blocked / already in use
```sh
$ lsof | grep tomcat
$ netstat -aon | grep 8080
$ ps -efl | grep java
$ ps -awwef | grep tomcat
$ kill -15 <tomcat pid>
```

### Avoid kill -9
NEVER kill a process with signal -9, because this type of killing process leaves its resources present in the system, which can only be removed after a server reboot.
Only use kill -9 only in extreme emergency. better to use kill -15, as it might take some time to cleanup resources, but you would always get proper flushing of that whole set of resources, that the process is consuming.
