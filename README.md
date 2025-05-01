# Automated Deployment of Personal Portfolio Website
This project demonstrates the implementation of a Continuous Integration/Continuous Delivery (CI/CD) pipeline for a personal portfolio website hosted on AWS. **The goal is to automate the deployment process, ensuring that any updates to the website's source code are automatically built and deployed, resulting in a faster and more efficient update cycle.**

This project involves building a simple personal portfolio website showcasing a user's skills, projects, and contact information. *The key aspect is automating the deployment of this website whenever teh dev team make changes to its source code*. This will be achieved by setting up a Continuous Integration/Continuous Delivery (CI/CD) pipeline on AWS.

## Core Functionality:
**1. Static Website:** A basic personal portfolio website built using HTML, CSS, and JavaScript. It should include sections like "About Me," "Projects," "Skills," and "Contact."

**2. Version Control:** The website's source code will be managed in an AWS CodeCommit repository.

**3. Continuous Integration:** Whenever changes are pushed to the CodeCommit repository (specifically to the main branch), AWS CodeBuild will automatically build the website (though for a static site, this step might be minimal or involve tasks like optimizing assets).

**4. Continuous Delivery:** Once the build process is successful, AWS CodeDeploy will automatically deploy the updated website files to an Amazon S3 bucket configured for static website hosting.

**5. Content Delivery Network (CDN):** Amazon CloudFront will be used to distribute the website content globally with low latency and improved performance.

**6. Custom Domain (Optional):** Configure a custom domain name (e.g., yourname.com) using Amazon Route 53 to access your portfolio.

**7. HTTPS (Optional):** Secure the website with HTTPS using an SSL/TLS certificate provided by AWS Certificate Manager (ACM).

## Architecture

  ![Alt text](Automated-Deployment-of-Personal-Portfolio-Website.drawio(1).png)

 The architecture involves the following flow:
 1.  **Code Changes:** Website source code is managed in an AWS CodeCommit repository.
 2.  **Trigger:** Pushing changes to the `main` branch of the CodeCommit repository triggers the CI/CD pipeline.
 3.  **Build (AWS CodeBuild):** AWS CodeBuild automatically checks out the code and executes the build steps defined in `buildspec.yml`. For this static website, the "build" phase primarily involves copying files.
 4.  **Deploy (AWS CodeDeploy):** Upon a successful build, AWS CodeDeploy deploys the website files to the designated Amazon S3 bucket configured for static website hosting, based on the instructions in `appspec.yml`.
 5.  **Content Delivery (Amazon CloudFront):** Amazon CloudFront serves as a CDN, distributing the website content globally from the S3 bucket, providing faster loading times and improved performance for users.
 6.   **(Optional) Custom Domain & HTTPS:** Amazon Route 53 manages the custom domain, pointing it to the CloudFront distribution, and AWS Certificate Manager provides the SSL/TLS certificate for secure HTTPS access.

## Technologies Used
* **AWS Services:**
    * Amazon S3
    * Amazon CloudFront
    * ~~AWS CodeCommit~~ Github
    * AWS CodeBuild
    * AWS CodeDeploy
    * AWS IAM
    * (Optional) Amazon Route 53
    * (Optional) AWS Certificate Manager (ACM)
* **Website Technologies:**
    * HTML
    * CSS
    * JavaScript

## Architecture
* (To be included, a high-level architecture diagram here.)

 The architecture involves the following flow:
 1.  **Code Changes:** Website source code is managed in an ~~AWS CodeCommit~~ Github repository.
 2.  **Trigger:** Pushing changes to the `main` branch of the ~~CodeCommit~~ Github repository triggers the CI/CD pipeline.
 3.  **Build (AWS CodeBuild):** AWS CodeBuild automatically checks out the code and executes the build steps defined in `buildspec.yml`. For this static website, the "build" phase primarily involves copying files.
 4.  **Deploy (AWS CodeDeploy):** Upon a successful build, AWS CodeDeploy deploys the website files to the designated Amazon S3 bucket configured for static website hosting, based on the instructions in `appspec.yml`.
 5.  **Content Delivery (Amazon CloudFront):** Amazon CloudFront serves as a CDN, distributing the website content globally from the S3 bucket, providing faster loading times and improved performance for users.
 6.   **(Optional) Custom Domain & HTTPS:** Amazon Route 53 manages the custom domain, pointing it to the CloudFront distribution, and AWS Certificate Manager provides the SSL/TLS certificate for secure HTTPS access.

## Implementation Details
### 1. Static Website
* A simple personal portfolio website was created with sections for "About Me," "Projects," "Skills," and "Contact."
* The source code is organized logically for easy maintenance.
### 2. ~~AWS CodeCommit~~ Github
* A Git repository was created in ~~AWS CodeCommit~~ Github to host the website's source code, enabling version control and collaboration (if appli
### 3. Amazon S3
* An S3 bucket was created and configured for static website hosting.
* Appropriate public access settings were applied to allow users to view the website.
### 4. AWS CodeBuild
* A CodeBuild project was set up, connected to the ~~CodeCommit~~ Github repository, with the `main` branch as the source.
* The `buildspec.yml` file defines the build environment and commands (e.g., copying files to the artifact directory).

    ```yaml
    version: 0.2

    phases:
      build:
        commands:
          echo "Building static website..."
          # For a simple static site, this might just be preparing artifacts
          - aws s3 sync . $CODEBUILD_SRC_DIR --exclude ".git*"

    artifacts:
      files:
        - '**/*'
      base-directory: $CODEBUILD_SRC_DIR
      discard-paths: yes
    ```
### 5. AWS CodeDeploy
* A CodeDeploy application and deployment group were created, targeting the S3 bucket.
* The deployment type was set to "In-place" for updating the files directly in the S3 bucket.
* An IAM service role was configured to grant CodeDeploy the necessary permissions to access S3.
* The `appspec.yml` file defines how the files from the CodeBuild artifact should be deployed to the S3 bucket.

    ```yaml
    version: 0.0
    os: linux
    files:
      - source: /
        destination: /
    ```
### 6. AWS IAM
* Specific IAM roles were created for CodeBuild and CodeDeploy, adhering to the principle of least privilege, granting them only the necessary permissions to interact with CodeCommit, S3, and other relevant services.
### 7. Amazon CloudFront
* A CloudFront distribution was created with the S3 static website endpoint as its origin.
* Default cache behavior was configured for optimal performance.
 ### 8. (Optional) Amazon Route 53 & AWS Certificate Manager (ACM)

* A custom domain (e.g., `yourportfolio.com`) to be configured in Route 53 to point to the CloudFront distribution's domain name.
* An SSL/TLS certificate to be requested and validated through ACM and associated with the CloudFront distribution to enable HTTPS.

## Challenges Faced and Solutions
*(Document any challenges  encountered during the project and how I resolved them. Examples may include issues with IAM permissions, configuring CodeDeploy to work with S3, troubleshooting build failures, etc.)*

## Lessons Learned
*(Briefly describe what I learned from this project, such as the benefits of CI/CD, the interaction between different AWS services, and best practices for static website hosting.)*

## Future Enhancements
*(List of potential future improvements or features that could be add to this project, such as:*
* *Adding a more complex build process (e.g., using a static site generator).*
* *Implementing automated testing as part of the CI pipeline.*
* *Setting up notifications for pipeline status changes.*
* *Exploring different deployment strategies.*

## Link to Code
*(Link to AWS CodeCommit repository or a mirror on GitHub.)*

## Live Demo
*(URL of live portfolio website hosted on AWS.)*
