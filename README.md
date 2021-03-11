whiterabbit-wordpress - Installation Instructions
================


Installing Docker In Amazon Linux 2
Please follow the below commands to install Docker in Amazon Linux :-

$ sudo yum install docker -y

$ sudo usermod -a -G docker ec2-user

$ sudo service docker restart

$ sudo chkconfig docker on



Installing Docker-Compose
Then we need to install Docker-Compose. Please follow below commands to install Docker-Compose :-

```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```
