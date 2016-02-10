#### ppbegdocker
####1
- 1-1
basic commands:
```
docker ps
docker inspect
docker logs
docker stop
docker kill
docker rm
```

- 1-4
```
docker run -t -i ubuntu /bin/bash
```

- 2-1
```
docker run ubuntu ls
docker ps -a
docker run --rm ubuntu ping google.com (delete after ping)
docker run --rm -i -t ubuntu bash
docker run --rm -i -t ubuntu apt-get install vim
docker run --rm -i -t ubuntu /bin/bash -c "apt-get install -y vim && vim"
```
- 2-2
```
docker run -d ubintu ping google.com //create a new container
docker inspect procname/hash
docker logs -f procname
docker ps -lq  (l=last container we made, q=only show id)
docker logs `docker ps -lq`
docker stop id
docker rm id
docker ps -aq | sargs docker rm -f
```
- 2-3
basic commands
```
docker images
docker run
docker diff
docker commit
```

others:
```
echo 'root:pass' | chpasswd
```

- 3-1
Dockerfile
```
FROM ubuntu

MAINTAINER H Ke<xxx@xxx.com>

RUN apt-get update && apt-get install -y openssh-server

RUN mkdir -p /var/run/sshd
```
- 3-2
set default container properties
```
docker run --rm -it author/sshd-examp cat /etc/ssh/sshd_config > sshd_config
```
Add properties in Dockerfile:
```
ADD sshd_config /etc/ssh/sshd_config
```
rebuild image:
```
docker build -t author/sshd-examp .
docker run --rm -it author/sshd-examp bash
```
check 'port' in file
```
grep -i port /etc/ssh/sshd_config
```
- 3-3
Add properties in Dockerfile:
```
CMD /usr/sbin/sshd -D (recommended)
(equivs to)
ENTRYPOINT /usr/sbin/sshd

USER nobody
WORKDIR /tmp
ENV foobar

EXPOSE 2222 (set ssh to 2222)
```
Then
```
docker build -t author/sshd-examp .
docker run -d author/sshd-examp
```

- 3-5


