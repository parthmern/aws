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
