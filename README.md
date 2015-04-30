docker build -t deployer .
docker run -d -v /var/run/docker.sock:/tmp/docker.sock deployer

## LOAD test
docker run -ti --name siegecmd centminmod/docker-centos6-siege /bin/bash