### Hosting a Static Website on Amazon S3 ###

### WorkFlow ###

- Developer updates website files locally  
- Files are uploaded to S3 via console 
- S3 serves content to users through the public endpoint  
- CloudFront caches content for global and secure delivery

S3 is a scalable & durable solution to storing and retrieving any amount of data, at any time, from anywhere without managing servers.
Hosting a website on S3 eliminates the need for infrastructure management while ensuring global availability, high durability.

### Overview ###

- This project & architecture illustrates the flow of hosting a static website on AWS. The recommended approach is to use S3. 
- The bucket serves as the origin and CloudFront to distribute the content.
- Its the most cost-effective way to deploy a website without managing servers.
- S3 serves as both the storage and web hosting platform for delivering cost-effective content globally with high durability and scalability.


### Purpose and Motivation ###

The purpose of this project is to:
- Understand S3 static website hosting 
- Demonstrate serverless web hosting on AWS  
- Showcase security, scalability, and cost optimization best practices 


### AWS Services Used ###

Amazon S3 – Stores website files and hosts them publicly.
AWS IAM – Controls access permissions to the S3 bucket.
CloudFront – Adds global caching, HTTPS, and faster delivery of website content to users.

### Key Takeaways ###

- Amazon CloudFront is a content delivery network (CDN) service. 
Upon DNS resolution by Route 53, the client’s request hits CloudFront, which may either serve cached content (for speed) or request the original content from the S3 bucket if it’s not already cached.
- Uses the SSL certificate to ensure HTTPS communication.
- This solution has two primary benefits:
the convenience of caching static content at edge location. 
the ability to define web access control lists (web ACLs) for the CloudFront distribution, which helps you secure requests to the content with minimal configuration

- CloudFront Function is designed for HTTP redirects. Let’s suppose someone types https://www.i-love-diving.com into their browser. 
Instead of staying on the ‘www’ version, this function quickly redirected them to the root domain https://i-love-diving.com (HTTP status 301). This provides a consistent domain experience. 

- Private S3 Bucket: storage where the website’s static assets (HTML, CSS, JS, images) are stored.
It’s designated as “private”, meaning direct public access is restricted. Only CloudFront, with its OAC, can fetch content from this bucket.

- Static Web Files contains the static content of the website, such as HTML & Image files.
These files were uploaded to the private S3 bucket, from where they are served to the end-users through the CloudFront distribution.
In summary, this architecture provides a highly available and scalable way to serve a static website with low latency.


### Well Architectured Framework Alignment ###
 Pillar | Implementation | Best Practices |
|--------|----------------|----------------|
| **Operational Excellence** | Serverless deployment with automated uploads | Use CI/CD for updates; monitor using CloudWatch or S3 events |
| **Security** | IAM roles, bucket policies, HTTPS | Apply least privilege; enforce encryption (SSE-S3/KMS); Block Public Access unless necessary |
| **Reliability** | Multi-AZ data replication | Enabled versioning;  cross-region replication |
| **Performance Efficiency** | S3 scales automatically; CloudFront caching | Optimize object sizes; enable Transfer Acceleration for global users |
| **Cost Optimization** | Pay-per-use storage and requests | lifecycle policies to move old files into different storage tiers |
| **Sustainability** | AWS-managed energy-efficient infrastructure | Shared data centers reduce environmental impact |

### Potential Enhancements ###

- Utilise Route 53 for Domain Name System management
When the client requests the website, the first thing that happens is a DNS query. 
This query is resolved by Route 53 to point towards the appropriate CloudFront distribution.

- AWS Certificate Manager  responsible for provisioning, managing, and deploying public and private SSL/TLS certificates.
The certificate ensures that the website connection remains encrypted and is indicated by “HTTPS” in the URL.
The CloudFront Distribution fetches the SSL certificate from the Certificate Manager to ensure an HTTPS-only communication with the client.

- Implement S3 object lifecycle rules for cost optimization  
- Enable Access Logging for auditing
- Automate deployment with GitHub Actions → S3 sync


### In conconlusion ###
This project demonstrates serverless, secure, scalable, and cost-efficient web hosting using Amazon S3.  
It highlights AWS best practices via the Well-Architected Framework and provides a knowledge framework connecting storage, security, and global performance concepts.
