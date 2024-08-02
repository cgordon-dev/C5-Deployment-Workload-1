# Cloud Deployment Project: AWS Elastic Beanstalk & Jenkins CI/CD Pipeline

## PROJECT GOAL

In this project, I focused on deploying a Retail Bank's application to the cloud using AWS Elastic Beanstalk, which is a fully managed service by AWS. Additionally, I set up a CI/CD pipeline with Jenkins to automate the deployment process. The main objective here was to ensure that the application is continuously tested, integrated, and deployed with minimal manual intervention, aiming to streamline the workflow for developers and maintain a smooth operation.

## PROJECT STEPS

### 1. Cloning the Repository
- **Purpose:** I started by cloning the repository, which contains the source code and essential configuration files.
- **Importance:** Cloning the correct codebase is crucial to ensure I’m working with the latest and most accurate version, which is fundamental for a successful deployment.

### 2. Setting Up an EC2 Instance
- **Purpose:** AWS EC2 was used to create an environment for Jenkins to run.
- **Importance:** This setup is vital because it provides Jenkins with a stable and dedicated environment, ensuring that it operates reliably throughout the project.

### 3. Installing Jenkins on EC2
- **Purpose:** Jenkins plays a central role in this CI/CD pipeline, automating tasks such as building and deploying the application.
- **Importance:** Jenkins is essential for implementing continuous integration and deployment, which are key practices in modern DevOps workflows.

### 4. Configuring Jenkins with GitHub
- **Purpose:** To enable Jenkins to access the source code stored in GitHub.
- **Importance:** By connecting Jenkins to GitHub, I ensured that any code changes trigger Jenkins to start building and testing automatically, keeping the code in a deployable state.
  
![Jenkins Deployment](/images/jenkins-deployment-successful.png)

### 5. Creating a Multi-Branch Pipeline in Jenkins
- **Purpose:** This step allows Jenkins to handle different branches for various environments like development, staging, and production.
- **Importance:** It’s crucial for ensuring that the right code is deployed to the correct environment without errors or mix-ups.

### 6. Linking GitHub Repository to Jenkins
- **Purpose:** Jenkins needs to pull the code from GitHub and know how to build it.
- **Importance:** This connection is the backbone of the CI/CD pipeline, facilitating a smooth transition from code commits to deployment.

### 7. Deploying the Application to AWS Elastic Beanstalk
- **Purpose:** AWS Elastic Beanstalk simplifies the deployment and management of the application.
- **Importance:** Using Elastic Beanstalk automates tasks like scaling, load balancing, and monitoring, which reduces the operational burden and allows me to focus on other aspects of the deployment.

## SYSTEM DESIGN DIAGRAM

![System Design Diagram](/images/cicd-pipeline-system-diagram.png)

### Diagram Details:
- **Tool Used:** I created the system design diagram using [draw.io](https://app.diagrams.net/).
- **Diagram Overview:** It visualizes the interactions between the EC2 instance, Jenkins, GitHub, and AWS Elastic Beanstalk, showing how each component connects within the deployment pipeline.

## ISSUES & TROUBLESHOOTING

### 1. 502 Bad Gateway Error
- **Issue:** I encountered a 502 Bad Gateway Error during the deployment to Elastic Beanstalk.
- **Solution:** The problem was traced back to the .zip file structure. Removing the parent directory from the .zip before uploading resolved the issue.
- **Lesson Learned:** Always double-check the directory structure before deploying to avoid such errors.

## OPTIMIZATION INSIGHTS

### Advantages of Using Managed Services
- **Scalability:** AWS Elastic Beanstalk scales the infrastructure automatically based on demand, which is a significant advantage.
- **Cost Efficiency:** Managed services can be cost-effective since AWS handles maintenance, updates, and scaling.
- **Security:** AWS provides built-in security features, helping to protect the application from potential threats.

### Challenges and Considerations
- **Vendor Lock-In:** Heavy reliance on a single cloud provider could lead to vendor lock-in.
  - **Mitigation:** To counter this, I’d consider a multi-cloud strategy or explore ways to abstract services to reduce dependency on one provider.
- **Limited Customization:** Managed services sometimes offer less control compared to self-managed solutions.
  - **Approach:** It’s crucial to assess whether a managed service meets all requirements. If not, a hybrid approach might be more suitable.

### Downsides of Elastic Beanstalk
- **Deployment Latency:** Automated deployments might be slower due to the additional layers of abstraction.
- **Reduced Control:** Elastic Beanstalk abstracts much of the underlying infrastructure, which can be limiting for those who need more granular control.

## FINAL THOUGHTS

This project was my first hands-on experience with deploying an application using AWS Elastic Beanstalk and setting up a CI/CD pipeline with Jenkins. Despite facing some challenges, like the 502 Bad Gateway Error, I was able to troubleshoot effectively by consulting documentation and conducting online research. Overall, this project was an excellent learning opportunity, providing me with a solid foundation in cloud deployment and CI/CD practices. I’m looking forward to applying these skills in future projects.
