# ntfy
ntfy with own secure server, for notification service

## Some important links

Server config file [server.yml](https://github.com/binwiederhier/ntfy/blob/main/server/server.yml)

NTFY DOCS: https://docs.ntfy.sh/

## Basic Setup

```
sudo docker run -p 80:80 -itd binwiederhier/ntfy serve
```

## Advanced setup

Create a `server.yml` at location `/etc/ntfy/server.yml`

Create the container
```
sudo docker run \
-v /var/cache/ntfy:/var/cache/ntfy \
-v /etc/ntfy:/etc/ntfy \
-p 80:80 \
-itd \
binwiederhier/ntfy \
serve \
--cache-file /var/cache/ntfy/cache.db
```
you can use it with default, `https://ntfy.sh` server.
but if you want to host your own server,

here you go:)

## Add a cloudfare tunnel via docker container 
![image](https://github.com/Alt-Shivam/ntfy/assets/81817735/48ed307d-bab6-41c4-a278-25178a7025ab)
* click next, and choose docker
* copy the docker run command, and paste on your host machine, or cloud machine, and run it.
* you can see the machine is attached to cloudfare tunnel as a connecter with id. press next.
* enter the details of sub-domain, domain.
* choose `http` and local ip on which ntfy is accessible.

and now you can make remote request to your server.

### Create a admin user
Login inside docker container:
```
docker exec -it <id-container> /bin/sh
ntfy user add --role=admin <username>
```

### Make a request
```
curl -u <username>:'<password>' -d "Hey, there" https://<subdomain>.domain.com/<topic>
```
