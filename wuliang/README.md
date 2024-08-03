## develop

```shell
# install docker
# https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```


```shell
# clone source code
git clone https://github.com/wulianglongrd/ztunnel -b test-branch

# build image
docker build -t wuliang/ztunnel-dev:0.1 -f wuliang/Dockerfile .

# run container
docker run -d --privileged -p 127.0.0.1:2222:22 --name wuliang-ztunnel-dev --mount type=bind,source="$PWD",target="/home/user/ztunnel" wuliang/ztunnel-dev:0.1

# login container use ssh
ssh user@localhost -p2222
sudo chown -R user:user ztunnel/
```
