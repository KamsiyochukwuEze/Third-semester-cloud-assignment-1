# Third-semester-cloud-assignment-1
### Task 1: Static Website Hosting Using S3 + IAM User with Limited Permissions
### Task 2: VPC Design for CloudLaunch Environment <br/> <br/>

## Task 1
### 🛠️Created the following S3 bucket for static website hosting:
<li>Cloudlaunch-site-bucket (Publicly accessible for anonymous users)</li> <br/>
<li>Cloudlaunch-private-bucket (Only accessible to designated IAM user to <code>GetObject</code> and <code>PutObject</code>)</li>  <br/>
<li>Cloudlaunch-visible-only-bucket(Only available be listed but not dispalyed)</li>  <br/>

### :heavy_plus_sign: Uploaded Static web files(Html,CSS,Js) to Cloudlaunch-site-bucket
<li>Set up a CloudFront distribution in front of this bucket for HTTPS and global caching.</li><br/>  
<li> S3 static site link: http://cloudlaunch-site-bucket.s3-website-eu-west-1.amazonaws.com</li></br>
<li>CloudFront Distribution Domain URL: https://dy3pjfue69g78.cloudfront.net/ </li>

