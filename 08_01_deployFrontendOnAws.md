### storage and distribution

#### storage
- every cloud provider has then to store object like mp4,mp3,img
- aws has S3 - simple storage 3

#### distribution
- CDN ( content delivery network ) 
- when u upload image on s3 it will give you link but here that link is not wokring directly
- so we have to create cloudfront distribution and then told to about s3 bucket list
- and everytime when users ask for file it goes to source means here s3 bucket in any corner and then it cached to that area cdn network for sometime ( known as POP= Point of Presence )

<br/>
- so for fronetend data serving using CDN

#### why not for backend
- if 100 people are asking for one img file then all users are going to get similar data
- but in backend for everyusers the data res is going to be different so there is not any meaning of caching data

<br/>

#### POP= Point of Presence AND SOURCE is only one
- why we are not creating multiple source storage for same data bcz that is expensive

