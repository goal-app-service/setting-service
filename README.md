# setting-service
Service for settings/scripts. 

Jenkins:
- build and run container: jenkins-script.sh
```
docker build -t jenkins-docker .

docker run -it --name jenkins-docker -p 8080:8080 -p 50000:50000 \
    -v jenkins_home:/var/jenkins_home \
    -v /var/run/docker.sock:/var/run/docker.sock \
    --restart unless-stopped \
    jenkins-docker
```
- start container: start-jenkins.sh 
```
docker container start jenkins-docker
```
- stop container: stop-jenkins.sh
```
docker container stop jenkins-docker
```
- remove container: remove-container.sh
```
docker rm --force jenkins-docker
```