docker build -t deployer .
 docker run -d -v /var/run/docker.sock:/tmp/docker.sock deployer