# Cloud Deployment Project: AWS Elastic Beanstalk & Jenkins CI/CD Pipeline

## PROJECT GOAL

In this project, the goal was to deploy a Retail Bank's application to the cloud using AWS Elastic Beanstalk, which is a fully managed service by AWS. I set up a CI/CD pipeline with Jenkins to automate the deployment process. The main objective here was to ensure that the application is continuously tested, integrated, and deployed with minimal manual intervention, aiming to streamline the workflow for developers and maintain a smooth operation.

---

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
  
### 5. Creating a Multi-Branch Pipeline in Jenkins
- **Purpose:** This step allows Jenkins to handle different branches for various environments like development, staging, and production.
- **Importance:** It’s crucial for ensuring that the right code is deployed to the correct environment without errors or mix-ups.

### 6. Linking GitHub Repository to Jenkins
- **Purpose:** Jenkins needs to pull the code from GitHub and know how to build it.
- **Importance:** This connection is the backbone of the CI/CD pipeline, facilitating a smooth transition from code commits to deployment.

![Jenkins Deployment](/images/jenkins-deployment-successful.png)

### 7. Deploying the Application to AWS Elastic Beanstalk
- **Purpose:** AWS Elastic Beanstalk simplifies the deployment and management of the application.
- **Importance:** Using Elastic Beanstalk automates tasks like scaling, load balancing, and monitoring, which reduces the operational burden and allows me to focus on other aspects of the deployment.

![Application](/images/application-homepage.png)

---

## SYSTEM DESIGN DIAGRAM

![System Design Diagram](/images/cicd-pipeline-system-diagram.png)

- **Tool Used:** I created the system design diagram using [draw.io](https://app.diagrams.net/).

### Overview:
The diagram illustrates the end-to-end CI/CD pipeline setup for deploying an application using Jenkins and AWS Elastic Beanstalk. Here’s how the system components interact:

1. **GitHub Repository:** The process starts with developers pushing code to the GitHub repository. This repository contains all the source code required for the application.

2. **Jenkins on EC2 Instance:** Jenkins, hosted on an AWS EC2 instance, pulls the latest code from the GitHub repository. The EC2 instance is configured with the necessary security groups to allow communication via SSH, HTTPS, and custom TCP ports.

3. **Build and Test:** Jenkins builds the code and runs automated tests to ensure the code is functioning as expected.

4. **Deployment to AWS Elastic Beanstalk:** Once the code passes the tests, Jenkins deploys the application to AWS Elastic Beanstalk. Elastic Beanstalk manages the application environment, handling tasks like load balancing, auto-scaling, and monitoring.

5. **IAM Roles:** Two IAM roles are depicted in the diagram:
   - One ensures that Jenkins has the necessary permissions to automate deployments and manage logging.
   - The other allows Elastic Beanstalk to provision and manage AWS resources securely, enabling the application to run and scale effectively.

This diagram showcases how the CI/CD pipeline automates the process from code commit to deployment, ensuring that the application is always in a deployable state while leveraging the scalability and management features of AWS Elastic Beanstalk.

---

## ISSUES & TROUBLESHOOTING

### 1. 502 Bad Gateway Error
- **Issue:** I encountered a 502 Bad Gateway Error during the deployment to Elastic Beanstalk.
- **Solution:** The problem was traced back to the .zip file structure. Removing the parent directory from the .zip before uploading resolved the issue.
- **Lesson Learned:** Always double-check the directory structure before deploying to avoid such errors.

---

## OPTIMIZATION INSIGHTS

### Advantages of Using Managed Services
- **Scalability:** AWS Elastic Beanstalk scales the infrastructure automatically based on demand, which is a significant advantage.
- **Cost Efficiency:** Managed services can be cost-effective since AWS handles maintenance, updates, and scaling.
- **Security:** AWS provides built-in security features, helping to protect the application from potential threats.

---

### Challenges and Considerations
- **Vendor Lock-In:** Heavy reliance on a single cloud provider could lead to vendor lock-in.
  - **Mitigation:** To counter this, I’d consider a multi-cloud strategy or explore ways to abstract services to reduce dependency on one provider.
- **Limited Customization:** Managed services sometimes offer less control compared to self-managed solutions.
  - **Approach:** It’s crucial to assess whether a managed service meets all requirements. If not, a hybrid approach might be more suitable.

### Downsides of Elastic Beanstalk
- **Deployment Latency:** Automated deployments might be slower due to the additional layers of abstraction.
- **Reduced Control:** Elastic Beanstalk abstracts much of the underlying infrastructure, which can be limiting for those who need more granular control.

---

## FINAL THOUGHTS

This project was my first hands-on experience with deploying an application using AWS Elastic Beanstalk and setting up a CI/CD pipeline with Jenkins. Despite facing some challenges, like the 502 Bad Gateway Error, I was able to troubleshoot effectively by consulting documentation and conducting online research. Overall, this project was an excellent learning opportunity, providing me with a solid foundation in cloud deployment and CI/CD practices. I’m looking forward to applying these skills in future projects.
