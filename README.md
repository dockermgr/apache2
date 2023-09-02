## 👋 Welcome to apache2 🚀  

Description  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update apache2
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/apache2/rootfs"
git clone "https://github.com/dockermgr/apache2" "$HOME/.local/share/CasjaysDev/dockermgr/apache2"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/apache2/rootfs/." "$HOME/.local/share/srv/docker/apache2/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-apache2 \
--hostname apache2 \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-apache2/rootfs/data:/data:z" \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-apache2/rootfs/config:/config:z" \
-p 80:80 \
casjaysdevdocker/apache2:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/apache2
    container_name: casjaysdevdocker-apache2
    environment:
      - TZ=America/New_York
      - HOSTNAME=apache2
    volumes:
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-apache2/rootfs/data:/data:z"
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-apache2/rootfs/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/apache2
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/apache2" "$HOME/Projects/github/casjaysdevdocker/apache2"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/apache2"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
