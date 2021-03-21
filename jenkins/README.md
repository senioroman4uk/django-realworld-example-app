# Example to setup jenkins with docker in docker

Docker compose to launch  preconfigured jenkins with configuration as a code and docker as a separate container (docker in docker approach). 
> Note that using docker in docker is [not recommended](https://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/), prefered option would be to share docker.sock from the host, but it does not work on mac due to [this issue](https://github.com/docker/for-mac/issues/4755)). Alternativly on linux we could use [sysbox jenkins container](https://blog.nestybox.com/2019/09/29/jenkins.html) that eliminates this problem alltogether

## Getting started
* install docker https://docs.docker.com/get-docker/
* fork this repository
* configure admin password in [docker-compose](./docker-compose.yaml)
* launch jenkins containers via docker-compose up
* go to http://localhost:8080/blue and authenticate (login: admin, password: the one that you specified in docker-compose)
* now create a new pipeline for your forked repository
If you want to add additional plugins modify [plugins.txt](./plugins.txt)
* Jenkins configuration as a code can be found in [casc.yaml](./casc.yaml)


## References
- [Jenkins setup on docker](https://www.jenkins.io/doc/book/installing/docker/)
- [How to automate Jenkins setup with docker and infrastructure as a code](https://www.digitalocean.com/community/tutorials/how-to-automate-jenkins-setup-with-docker-and-jenkins-configuration-as-code)
- [Fix for "Invalid agent type "docker" specified. Must be one of [any, label, none]."](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/Fix-Jenkins-Invalid-agent-type-Docker-specified-any-label-none-error#:~:text=Jenkins%20Docker%20error%3A%20Invalid%20agent%20type&text=Invalid%20agent%20type%20%22docker%22%20specified,the%20Jenkins%20Docker%20Pipeline%20plugin) 
- [do not use docker in docker for your ci testing](https://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/)
- [Docker 2.3.2.0 and later yield permission denied for /var/run/docker.doc when using Docker in Docker](https://github.com/docker/for-mac/issues/4755)