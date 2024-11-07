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

- here is how to do for multiple ports ( https://chatgpt.com/share/672b7c89-99b4-8010-8787-1090cf6b4615 )
- make sure that the domain/url is pointing to the public ip where your ec2 instance/server is running in DNS/DOMAIN managaement
- for local testing u can do changes as below in /etc/hosts/


#### extra ( how to change hosts of your local machine)

- how to change host of your local machine like for specific url/domain hit this specific ip

```
sudo vi /etc/hosts 
// it opens hosts file like below
```

![image](https://github.com/user-attachments/assets/ce837e94-5fbb-491e-902c-322344e3ff18)

then change it to this

![image](https://github.com/user-attachments/assets/37d7bb5e-eaa0-474f-baa6-57d4023ecfc0)

here i  can see that for "parthmern.com" domain in my local machine i am hitting ip named "3.144.221.193" which is ip of my ngnix server right now

![image](https://github.com/user-attachments/assets/9abb7e72-65f0-445a-9ffa-f91736fbf3fc)

here above image i can see that for parthmern.com url my local machine here ec2 machine is hitting the ip "3.144.221.193" which i set on /etc/hosts config file

- here sometimes in local machine when u hit with chrome browser it redirects to the actual original ip eventhoug i changed it because of CACHING DNS techniques inshort caching so we can see it using cli or try with another browser

- IMP : ip cannot go beyong 255 as we know


