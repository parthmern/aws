### nginx

- nginx open source software for "reverse proxy", web serving ,load balancing, caching

- https://projects.100xdevs.com/tracks/g0AcDSPl74nk45ZZjRdU/aws-7

- assume that on your ec2 machine you are running 2 servers/services on port 8080 and 8081
- what i can do is i am running something else on port 80 which can decide that if the incoming url is backend1.com then send request on 8080 and if url is backend2.com then send request on 8081 and thar something else between thing is called as reverse proxy

- ( generally by default your public ip for machine is running on port 80)


![image](https://github.com/user-attachments/assets/b54014a2-433b-4dca-a916-7f5a23612f44)

#### install

```
sudo apt update
sudo apt install nginx

// This should start a nginx server on port 80
// Try visiting the website of ec2 public ip `http://ec2-3-144-221-193.us-east-2.compute.amazonaws.com/` like this which is directly hitting port 80 of ec2 machine so `http://ec2-3-144-221-193.us-east-2.compute.amazonaws.com:80` hit to the same page
// also that shows ngnix server webpage

```

#### create ngnix reverse proxy

```
sudo vi /etc/nginx/nginx.conf 
// this command shows the the shows the ngnix congifuration file


sudo rm sudo vi /etc/nginx/nginx.conf
// delete the default config file

```

- after deleting touch file and then do command `sudo vi /etc/nginx/nginx.conf` and edit as below

```

events {
    # Event directives...
}

http {
	server {
    listen 80;
    server_name be1.100xdevs.com;

    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
	}
}

```


#### extra

- how to change host of your local machine like for specific url/domain hit this specific ip

```
sudo vi /etc/hosts 
// it opens hosts file
```