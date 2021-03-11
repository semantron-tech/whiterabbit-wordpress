whiterabbit-wordpress - Installation Instructions
================


Installing Docker In Amazon Linux 2
Please follow the below commands to install Docker in Amazon Linux :-

$ sudo yum install docker -y

$ sudo usermod -a -G docker ec2-user

$ sudo service docker restart

$ sudo chkconfig docker on



Installing Docker-Compose
=========
Then we need to install Docker-Compose. Please follow below commands to install Docker-Compose :-

```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```


Creating Compose Directory
==========

To perform the compose, we can create a separeate compose directory : -

$ mkdir wordpress
$ cd wordpress


Creating ngix.conf
==========
```
$ cd wordpress
```

Enter the created directory and create a file named " nginx.conf " as following below :-

```
$ vim nginx.conf

server {
  listen 80;
  listen [::]:80;
  access_log off;
  root /var/www/html;
  index index.php;
  server_name example.com;
  server_tokens off;
  location / {
    # First attempt to serve request as file, then
    # as directory, then fall back to displaying a 404.
    try_files $uri $uri/ /index.php?$args;
  }
  # pass the PHP scripts to FastCGI server listening on wordpress:9000
  location ~ \.php$ {
    fastcgi_split_path_info ^(.+\.php)(/.+)$;
    fastcgi_pass wordpress:9000;
    fastcgi_index index.php;
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_param SCRIPT_NAME $fastcgi_script_name;
  }
}
```
