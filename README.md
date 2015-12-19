### ppbeginningdocker
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


