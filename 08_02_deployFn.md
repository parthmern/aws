## how to build project

- https://projects.100xdevs.com/tracks/w5E6PT2t0IyOFM3bZxcM/aws-fe-2

- This approach will not work for frameworks that use Server side rendering (like Next.js)
- This will work for basic React apps(convert jsx files to raw html and css,js), HTML/CSS/JS apps

<br/>
 
- when we build any app react app that makes DIST folder and then we try to open index.html insde that DIST folder but that is not working
- so we need server `npm i -g serve` then go to DIST folder and `serve` or `npx serve` run this now u are able to access page ( it servers all file from folder )
- even though we donot have react app but we can see the whole app from dist folder

### upload to s3 

- create s3 bucket and dragdrop all files under dist folder 
- then try to access index.html using object url but u are not able to access it

### Connecting Cloudfront

- go to cloudfront serveice
- while creating distribution 
- in "Origin path - optional" field if we uploaded the dist folder then we have to show the "dist/" into that but we uploaded the all files into root so donot have to put anything
- https://projects.100xdevs.com/tracks/w5E6PT2t0IyOFM3bZxcM/aws-fe-7
- follow above but in origin access control setting > go to origin access control > create new OAC > Sign requests > create now
- "Web Application Firewall (WAF)" > enable security protection
- and "Default root object - optional" > index.html ( this is for when someone visit cloudfront link directly it shows index.html page so this is alternative of  `<cloudfrontLink>` to `<cloudfrontLink>/index.html`)
- click on create 
- that gives you a new notification that "The S3 bucket policy needs to be updated" where copy the policy and then click on update policy 

<br/>

- now give permission acccess from your s3 bucket 
- go to the bucket > permission > click EDIT on bucket policy > and then Paste that copied policy from notification
- that shows that anything under bucket `arn:aws:s3:::parthmern-react-app-test/*` part is accessable from `arn:aws:cloudfront::147997145194:distribution/E3QNU8X8ABSQA` distribution

<br/>

- now go to distrubution that u created where u can get "Distribution domain name" link is `https://d2qd6kafiqzly6.cloudfront.net/` where your frontend is deployed 