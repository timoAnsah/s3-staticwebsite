### Hosting a Static Website on Amazon S3

### Overview
This project demonstrates how I host a static website on AWS. The recommended approach is to use S3
The bucket serves as the origin and I used Amazon CloudFront to distribute the content
simplest and most cost-effective way to deploy a website without managing servers.
S3 serves as both the storage and web hosting platform for delivering cost-effective content globally with high durability and scalability.

This solution has two primary benefits:
the convenience of caching static content at edge locations, and 
the ability to define web access control lists (web ACLs) for the CloudFront distribution, which helps you secure requests to the content with minimal configuration
### Purpose and Motivation
The goal of this project is to understand S3’s static website hosting capability for front-end websites.
This use case is ideal for portfolios, blogs...

### AWS Services Used
Amazon S3 – Stores website files and hosts them publicly.
AWS IAM – Controls access permissions to the S3 bucket.
CloudFront – Adds global caching, HTTPS, and faster delivery of website content to users.

### Key Takeaways
