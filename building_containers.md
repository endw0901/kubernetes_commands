# building containers

- download Docker Engine
- Windows:https://docs.docker.com/engine/installation/windows/

## dockerize nodejs app

- サンプルとしてnodejs appをdockerize


## build docker image

```
// bundled with ubuntuのdockerをinstall
sudo apt-get install docker.io
docker --version

sudo apt-get install git
// 開発者のgitをclone
git clone xxxxxxxxxxxxx/docker-demo
sudo usermod -G docker ubuntu
logout

// build docker
cd docker-demo
docker build .

//3000でrunするしすてむを3000にexpose
// -i : interactive mode
docker run -p 3000:3000 -it xxxxxx 
curl localhost:3000
```
