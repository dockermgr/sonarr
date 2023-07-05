## 👋 Welcome to sonarr 🚀  

sonarr README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update sonarr
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/sonarr/rootfs"
git clone "https://github.com/dockermgr/sonarr" "$HOME/.local/share/CasjaysDev/dockermgr/sonarr"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/sonarr/rootfs/." "$HOME/.local/share/srv/docker/sonarr/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-sonarr \
--hostname sonarr \
-e PUID=1000 \
-e PGID=1000 \
-e TZ=${TIMEZONE:-America/New_York} \
-v /mnt/tv:/tv:z \
-v /mnt/downloads:/downloads:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-sonarr/rootfs/config:/config:z \
-p 0.0.0.0:8989:8989 \
casjaysdevdocker/sonarr:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/sonarr
    container_name: casjaysdevdocker-sonarr
    environment:
      - TZ=America/New_York
      - HOSTNAME=sonarr
      - PUID=1000
      - PGID=1000
    volumes:
      - /mnt/tv:/tv:z
      - /mnt/downloads:/downloads:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-sonarr/rootfs/config:/config:z
    ports:
      - 0.0.0.0:8989:8989
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/sonarr
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/sonarr" "$HOME/Projects/github/casjaysdevdocker/sonarr"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/sonarr"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
