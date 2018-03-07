# Jenkins server configuration

## Install jenkins ubuntu 16.04

```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
echo deb https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list
sudo apt-get update
sudo apt-get install jenkins -y
sudo systemctl start jenkins
```

## Opening jenkins port

```bash
sudo ufw allow 8080
```

## Create key for jenkins so he can sign in to Github and Update status

```bash
sudo -u jenkins -i
ssh-keygen -t rsa
```

## Configure the user access to the repo (todo)

## Install php 

```bash
sudo apt-get install php php-sqlite3 php-apcu
```

## Install composer 

```bash
curl -sS https://getcomposer.org/installer -o composer-setup.php
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

## Install phpunit
```bash
sudo apt-get install phpunit 
```

## Install PHP plugins

### Download the cli on your local machine

```bash
wget http://your.server-url:8080/jnlpJars/jenkins-cli.jar
```

### Install plugins

From your local machine

```bash
java -jar jenkins-cli.jar -s http://jenkins.luisrosales.info:8080 install-plugin checkstyle cloverphp crap4j dry htmlpublisher jdepend plot pmd violations warnings xunit
```

### Restart

```bash
java -jar jenkins-cli.jar -s http://jenkins.luisrosales.info:8080 safe-restart
```

## Other Useful commands

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```