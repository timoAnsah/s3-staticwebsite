### Hosting a Static Website on Amazon S3

S3 is a scalable & durable solution to storing and retrieving any amount of data, at any time, from anywhere without managing servers .

### Overview
This project & architecture illustrates the flow of hosting a static website on AWS. The recommended approach is to use S3. 
The bucket serves as the origin and CloudFront to distribute the content.
Its the most cost-effective way to deploy a website without managing servers.
S3 serves as both the storage and web hosting platform for delivering cost-effective content globally with high durability and scalability.


### Purpose and Motivation
The goal of this project is to understand S3’s static website hosting capability for front-end websites.
This use case is ideal for portfolios, blogs...

### AWS Services Used
Amazon S3 – Stores website files and hosts them publicly.
AWS IAM – Controls access permissions to the S3 bucket.
CloudFront – Adds global caching, HTTPS, and faster delivery of website content to users.

### Key Takeaways 

Amazon CloudFront is a content delivery network (CDN) service. 
Upon DNS resolution by Route 53, the client’s request hits CloudFront, which may either serve cached content (for speed) or request the original content from the S3 bucket if it’s not already cached.
Uses the SSL certificate to ensure HTTPS communication.
This solution has two primary benefits:
the convenience of caching static content at edge location. 
the ability to define web access control lists (web ACLs) for the CloudFront distribution, which helps you secure requests to the content with minimal configuration

CloudFront Function: This function is designed for HTTP redirects. Let’s suppose someone types http://www.i-love-diving.s3-website.eu-west-2.amazonaws.com/ into their browser. 
Instead of staying on the ‘www’ version, this function quickly redirected them to the root domain https://i-love-diving.s3-website.eu-west-2.amazonaws.com/ (HTTP status 301). 
This provides a consistent domain experience.

Private S3 Bucket: storage where the website’s static assets (HTML, CSS, JS, images) are stored.
It’s designated as “private”, meaning direct public access is restricted. Only CloudFront, with its OAC, can fetch content from this bucket.

Static Web Files: Represents the static content of the website, such as HTML, CSS, and JavaScript files.
These files can be pushed or uploaded to the private S3 bucket, from where they are served to the end-users through the CloudFront distribution.
In summary, this architecture provides a highly available and scalable way to serve a static website with low latency

### Future Improvements
Utilise Route 53 for Domain Name System management
When the client requests the website, the first thing that happens is a DNS query. 
This query is resolved by Route 53 to point towards the appropriate CloudFront distribution.

AWS Certificate Manager  responsible for provisioning, managing, and deploying public and private SSL/TLS certificates.
The certificate ensures that the website connection remains encrypted and is indicated by “HTTPS” in the URL.
The CloudFront Distribution fetches the SSL certificate from the Certificate Manager to ensure an HTTPS-only communication with the client.
