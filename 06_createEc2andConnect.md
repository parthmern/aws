- go to aws search ec2 service and create FREE TIRED all specification

- "CONFIGURE KEY" is one key that will generate ".pem" key 

- create it then

- now go to that generated file and then chnage the user permission to READONLY ( in linux `chmod 400 filename`) Must step otherwise give error while connecting using ssh

- `ssh -i .\devops-practice.pem ubuntu@18.118.6.245` use to connect your ec2 machine where `ssh -i C:\path\to\private_key username@<hostname|publicIp>`

- DONOT FORGET TO STOP INSTANCE (go to instances page then tick mark it and on right corner there is instanceState btn click it and stop it)

- for windows ( use putty or https://youtu.be/CNzxsml8L-c?si=vJnzL7ohP7WIYaqz) and make sure that in security section of that instaace 22 port should be open for ssh connection 

- OR aws also provide cli go to instances select it and click on connect then again on connect will open cli for that ec2 machien

- after this while following the `https://projects.100xdevs.com/tracks/g0AcDSPl74nk45ZZjRdU/aws-6` file

- there is issue when we are not able to hit request on sepcific port on which node server is running so in that case we have to open that port with "custom tcp" connection in security groups of that instance for both iov4 and ipv6

## run nodejs server

- `git clone https://github.com/hkirat/sum-server` then 
- install nodejs in ec2 machine
- then `cd sum-server` and `npm install`
- then `node index.js`

- `npm i -g pm2` and then `pm2 start index.js` to run your app forever even though you close your CLI or exit from terminal
