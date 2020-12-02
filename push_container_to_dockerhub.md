# push container to Docker Hub
 
 - docker run ・・・docker app起動
 - locally built image => the Docker Regestory 
 - Docker Hub or AWS ECR
 
 ```
 docker login
 docker tag imageid your-login/docker-demo
 docker push your-login/docker-demo
 
 ```
 
 ## docker login
 
 ```
 docker login

 ```
 
 - create repository on docker Webサイト
 
 ```
 // tag the image
 docker tag exxxxxx xxxx/k8s-demo
 // imageとtag確認
 docker images
 docker push (nae)/(repository)
 ```
 
 - docker hubにuploadされたことを確認
 
 
 
 
 
