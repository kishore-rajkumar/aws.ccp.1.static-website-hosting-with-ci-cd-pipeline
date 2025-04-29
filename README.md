# aws.ccp.1.static-website-hosting-with-ci-cd-pipeline
This project involves building a simple personal portfolio website showcasing a user's skills, projects, and contact information. The key aspect is automating the deployment of this website whenever teh dev team make changes to its source code. This will be achieved by setting up a Continuous Integration/Continuous Delivery (CI/CD) pipeline on AWS.

# Automated Deployment of Personal Portfolio Website

## Overview
This project demonstrates the implementation of a Continuous Integration/Continuous Delivery (CI/CD) pipeline for a personal portfolio website hosted on AWS. The goal was to automate the deployment process, ensuring that any updates to the website's source code are automatically built and deployed, resulting in a faster and more efficient update cycle.

## Core Functionality:
**1. Static Website:** A basic personal portfolio website built using HTML, CSS, and JavaScript. It should include sections like "About Me," "Projects," "Skills," and "Contact."

**2. Version Control:** The website's source code will be managed in an AWS CodeCommit repository.

**3. Continuous Integration:** Whenever changes are pushed to the CodeCommit repository (specifically to the main branch), AWS CodeBuild will automatically build the website (though for a static site, this step might be minimal or involve tasks like optimizing assets).

**4. Continuous Delivery:** Once the build process is successful, AWS CodeDeploy will automatically deploy the updated website files to an Amazon S3 bucket configured for static website hosting.

**5. Content Delivery Network (CDN):** Amazon CloudFront will be used to distribute the website content globally with low latency and improved performance.

**6. Custom Domain (Optional):** Configure a custom domain name (e.g., yourname.com) using Amazon Route 53 to access your portfolio.

**7. HTTPS (Optional):** Secure the website with HTTPS using an SSL/TLS certificate provided by AWS Certificate Manager (ACM).

## Technologies Used
* **AWS Services:**
    * Amazon S3
    * Amazon CloudFront
    * AWS CodeCommit
    * AWS CodeBuild
    * AWS CodeDeploy
    * AWS IAM
    * (Optional) Amazon Route 53
    * (Optional) AWS Certificate Manager (ACM)
* **Website Technologies:**
    * HTML
    * CSS
    * JavaScript
