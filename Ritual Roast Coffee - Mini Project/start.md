## Build a VPC

![alt text](image.png)

![alt text](image-1.png)

![alt text](image-2.png)

![alt text](image-3.png)

![alt text](image-4.png)

## Create a Security Group

![alt text](image-5.png)

![alt text](image-6.png)

![alt text](image-7.png)

## Create an Amazon ECR Repository

![alt text](image-8.png)

## Create an IAM Role

![alt text](image-9.png)

![alt text](image-10.png)

![alt text](image-11.png)

## Create an Instance EC2

![alt text](image-12.png)

![alt text](image-13.png)

![alt text](image-14.png)

![alt text](image-15.png)

![alt text](image-16.png)

![alt text](image-17.png)

## Connect to instance

![alt text](image-19.png)

```bash
# Use root user
sudo su

# Add user
adduser [username]

# Add username to the sudo group
sudo usermod -aG sudo [username]

# Verify by switching to [username] and checking
su - danang

# Update package
sudo apt update -y
```

![alt text](image-21.png)

## Install Docker

```bash
# Install a few prerequisite packages which let apt use packages over HTTPS
sudo apt install apt-transport-https ca-certificates curl software-properties-common

# Then add the GPG key for the official Docker repository to your system
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Add the Docker repository to APT sources
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

# Make sure you are about to install from the Docker repo instead of the default Ubuntu repo
apt-cache policy docker-ce

# Finally, install Docker
sudo apt install docker-ce

# Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running
sudo systemctl status docker
```
