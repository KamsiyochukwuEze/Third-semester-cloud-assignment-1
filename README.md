# Third-semester-cloud-assignment-1
### Task 1: Static Website Hosting Using S3 + IAM User with Limited Permissions
### Task 2: VPC Design for CloudLaunch Environment <br/> <br/>

## Task 1
### 🛠️Created the following S3 bucket for static website hosting:
<li>✅Cloudlaunch-site-bucket (Publicly accessible for anonymous users)</li> <br/>
<li> ✅Cloudlaunch-private-bucket (Only accessible to designated IAM user to <code>GetObject</code> and <code>PutObject</code>)</li>  <br/>
<li> ✅Cloudlaunch-visible-only-bucket(Only available be listed but not dispalyed)</li>  <br/>

### :heavy_plus_sign: Uploaded Static web files(Html,CSS,Js) to Cloudlaunch-site-bucket
<li>Set up a CloudFront distribution in front of this bucket for HTTPS and global caching.</li><br/>  
<li> 🔗S3 static site link: http://cloudlaunch-site-bucket.s3-website-eu-west-1.amazonaws.com</li></br>
<li> 🔗CloudFront Distribution Domain URL: https://dy3pjfue69g78.cloudfront.net/ </li> </br>

### 👤 Created an IAM user named "cloudlaunch-user" and used JSON policy document to define and attach custom IAM policy. 

 ``` JSON
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Sid": "Statement2",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::cloudlaunch-private-bucket"
            ]
        },
        {
            "Sid": "Statement3",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::cloudlaunch-site-bucket"
            ]
        },
        {
            "Sid": "Statement4",
            "Effect": "Deny",
            "Action": [
                "s3:DeleteObject"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Sid": "Statement5",
            "Effect": "Deny",
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::cloudlaunch-visible-only-bucket"
            ]
        },
        {
            "Sid": "Statement6",
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeVpcs",
                "ec2:DescribeSubnets",
                "ec2:DescribeRouteTables",
                "ec2:DescribeSecurityGroups"
            ],
            "Resource": "*"
        }
    ]
} 
```

## Task 2
### :sparkles: Created a VPC named "cloudlaunch-vpc" with CIDR Block: 10.0.0.0/16. 
### :heavy_plus_sign: Created the following subnets in the VPC
<li>:white_check_mark: Public Subnet (10.0.1.0/24)</li>
<li>:white_check_mark: Application Subnet (10.0.2.0/24)</li>
<li>:white_check_mark: Database Subnet (10.0.3.0/24)</li>

### :globe_with_meridians: Created an Internet Gateway named "cloudlaunch-igw" and attached it to "cloudlaunch-vpc"

### :heavy_plus_sign: Route table for public subnet
#### ✨Created a route table named "cloudlaunch-public-rt" and associated it with the public subnet. 
#### 🌐 Added a route that sends all internet-bound traffic (0.0.0.0/0) to the Internet Gateway "cloudlaunch-igw"

### :heavy_plus_sign: Route table for private subnets
#### ✨ Created separate route tables for the Application and Database subnets named "cloudlaunch-app-rt" "cloudlaunch-db-rt" respectively. 
#### ⛔ Not associated with any Internet Gateway
#### ⛔ No route to 0.0.0.0/0 (Fully Private)

### ✨Security Groups 
#### Created two security groups 
<li> ✅"cloudlaunch-app-sg" that allows HTTP (port 80) access within the VPC only.</li>
<li> ✅"cloudlaunch-db-sg" that allows MySQL (port 3306) access from app subnet only</li>

### 👤 IAM Credentials:
<li>Cosole URL: https://cloudkamsi.signin.aws.amazon.com/console</li>
<li>Account Alias:cloudkamsi </li>



