[![](https://images.microbadger.com/badges/version/neomediatech/dovecot-honey-alpine.svg)](https://microbadger.com/images/neomediatech/dovecot-honey-alpine "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/neomediatech/dovecot-honey-alpine.svg)](https://microbadger.com/images/neomediatech/dovecot-honey-alpine)
![](https://img.shields.io/github/last-commit/Neomediatech/dovecot-honey-docker-alpine.svg?style=plastic)
![](https://img.shields.io/github/repo-size/Neomediatech/dovecot-honey-docker-alpine.svg?style=plastic)

# dovecot-honey-alpine
Dockerized version of Dovecot as honeypot service, based on Alpine Linux

## Usage
You can run this container with this command:  
`docker run -d --name dovecot-honey-alpine -p 110:110 -p 143:143 -p 993:993 -p 995:995 neomediatech/dovecot-honey-alpine`  

Logs are written inside the container, in /var/log/dovecot/dovecot.log, and on stdout. You can see realtime logs running this command:  
`docker logs -f dovecot-honey-alpine`  
`CTRL c` to stop seeing logs.  

If you want to map logs outside the container you can add:  
`-v /folder/path/on-host/logs/:/var/log/dovecot/`  
Where "/folder/path/on-host/logs/" is a folder inside your host. You have to create the host folder manually.  

You can run it on a compose file like this:  

```
version: '3'  

services:  
  dovecot:  
    image: neomediatech/dovecot-honey-alpine:latest  
    hostname: dovecot-honey  
    ports:  
      - '110:110'  
      - '143:143'  
      - '993:993'  
      - '995:995'  
```
Save on a file and then run:  
`docker stack deploy -c /your-docker-compose-file-just-created.yml dovecot-honey`

If you want to map logs outside the container you can add:  
```
    volumes:
      - /folder/path/on-host/logs/:/var/log/dovecot/
```
Where "/folder/path/on-host/logs/" is a folder inside your host. You have to create the host folder manually.

Save on a file and then run:  
`docker stack deploy -c /your-docker-compose-file-just-created.yml dovecot-honey`  
