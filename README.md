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
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-sonarr/rootfs/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-sonarr/rootfs/config:/config:z \
-p 80:80 \
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
    volumes:
      - $HOME/.local/share/srv/docker/casjaysdevdocker-sonarr/rootfs/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-sonarr/rootfs/config:/config:z
    ports:
      - 80:80
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
