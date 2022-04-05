# docker-raspberry-pi-nginx-proxy-manager
docker-raspberry-pi-nginx-proxy-manager

## REF: https://nginxproxymanager.com
## REF: https://hub.docker.com/r/jc21/nginx-proxy-manager

```
mkdir -p /opt/docker-compose
cd /opt/docker-compose
git clone git@github.com:ernestgwilsonii/docker-raspberry-pi-nginx-proxy-manager.git
cd docker-raspberry-pi-nginx-proxy-manager

sudo mkdir -p /opt/docker/nginx-proxy-manager/data
sudo mkdir -p /opt/docker/nginx-proxy-manager/letsencrypt
sudo chmod -R a+w /opt/docker/nginx-proxy-manager

docker pull jc21/nginx-proxy-manager:latest

# Perform basic tests
sudo docker-compose up
sudo docker-compose up -d
sudo docker-compose down

# http://IPAddressHere:81
# Default Admin User:
# Email:    admin@example.com
# Password: changeme

##########
# Deploy #
##########
# Deploy the stack into a Docker Swarm
sudo docker stack deploy -c docker-compose.yml nginx-proxy-manager
#sudo docker stack rm nginx-proxy-manager

# Verify
docker service ls | grep nginx-proxy-manager
docker service logs -f nginx-proxy-manager_app
```