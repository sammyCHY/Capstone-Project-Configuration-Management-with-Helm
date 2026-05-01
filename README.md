# Capstone Project: Configuration Management with Helm.

## Project Scenario.

In this Capstone project, you will embark on a journey to introduce you to the basics of Helm charts and their integration with Jenkins. As a DevOps Engineer, your goal is to design and implement a simplified CI/CD Pipeline using Jenkins, with a primary focus on Helm charts. The objective is to automate the deployment of a basic web application, promoting understanding and hands-on experience for those new to the field.


### Pre-requisite

   - Basic knowledge of Jenkins essentials.
   - Enthusiasm and completion of the Introduction to Helm Charts and working with Helm Charts mini Projects. 

    ## Project Deliverables

###  Documentation:

   - Documentation for each Helm chart component setup.
   - Explanation of simplified security measures implemented at each step.

### Demonstration:

   - Step-by-step demonstration of the CI/CD pipeline with Helm integration. 


## Project Components

Jenkins Server Setup.

**Objective:** Configure Jenkins server for a CI/CD Pipeline automation.

Below is the Jenkins Server created to Implement this project.

![The Image below shows the Configuration of Jenkins server for a CI/CD Pipeline automation](image/configuration-jenkins-helm-server.png)

### Steps:

1. Install Jenkins on a dedicated server (with detailed explanations). 

Below is the step by step process of Jenkins installation and configuration on the AWS Server

   - After creating The server for the jenkins installation (the server Image created for the installation is above) Although, I created "Ubuntu server" but still have other options of servers like; Redhat, Amazon Linux AWS, MacOS, Debian, Window etc.

   - ssh into the server and run "sudo apt update"
![The Image shows the ssh into the server](image/ssh-login-server.png)

   - Then run "sudo apt update"

![The Image shows the server update](image/sudo-apt-update.png)


Then, Jenkins Installation, You have to search for Jenkins official site and copy the linux Ubuntu package and Install on the server. The link here is the jenkins official site [click](https://www.jenkins.io/doc/book/installing/)

![The Image shows the official site](image/jenkins-official1.png)


![The Image shows the official site](image/jenkins-official2.png)

![The Image shows the official site](image/jenkins-official3.png)

![The Image shows the official site](image/jenkins-official4.png)

![The Image shows the official site](image/jenkins-official5.png)

![The Image shows the official site](image/jenkins-official6.png)


Before the Installation of Jenkins, Java package manager have to be installed first like openjdk-19,21, etc.

   `sudo apt update`
   `sudo apt install fontconfig openjdk-21-jre`
   `java -version`


  ```
  sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

![The Image shows Jenkins Installation](image/jenkins-installation.png)

After the Installation, access the server and configure the Inbound security group `8080 port` range.

![The Image shows the jenkins security group port configuration ](image/jenkins-server-port-configuration.png)

Login to the jenkins by copying the public Ip of the server then ":8080" and paste in a browser to finalize the activation.

![The Image shows the server-IP](image/server-ip.png)

![The Image shows the jenkins server-IP on the browser](image/jenkins-server-ip.png)

![The Image shows initial jenkins administrative password](image/jenkins-administrative-password.png)

![The Image shows initial jenkins administrative password](image/jenkins-administrative-password1.png)

![The Image shows initial jenkins administrative password](image/jenkins-administrative-password2.png)

![The Image shows initial jenkins administrative password](image/jenkins-administrative-password3.png)

![The Image shows initial jenkins administrative password](image/jenkins-administrative-password4.png)

![The Image shows initial jenkins administrative password](image/jenkins-administrative-password5.png)

![The Image shows initial jenkins administrative password](image/jenkins-hosted.png)


2. Set up necessary Plugins (Git, Helm, etc.) with simple configurations.


3. Configure Jenkins with basic security measures suitable for beginners.

### Instruction for Jenkins:

   - Provide step-by-step documentation for Jenkins installation.

   - Simplify the Plugin installation and configuration steps.

   - Outline basic security measures applied to the Jenkins server.


#### Helm Chart Basics

   - Objective: Introduce the fundamental concepts of Helm charts.

**Steps:**

1. Explain what Helm charts are and their purpose.



2. Walkthrough of creating a basic Helm chart for a web application.

3. Cover Helm chart templating basics.


Instructions:

   - Provide beginner-friendly explanations of Helm chart concepts.

   - Include a hands-on guide for creating a simple Helm chart.


### Working with Helm Charts 

**Objective:** Guide students in working with Helm charts for application deployment.

**Steps:**

1.  Deploy a sample web application using the Helm chart created.

2. Introduce values and templates in Helm Charts.

3. Explore upgrading and rolling back applications using Helm.


## Instructions:

- Include simple examples and explanations for deploying applications with Helm.

- Provide a guide for Helm chart customization.


### Integrating Helm with Jenkins.

**Objective: Integrate Helm with Jenkins for automated deployments.

### Steps:

1. Integrate Jenkins with Helm for deployment.

2. Configure Jenkins to use Helm charts in the CI/CD Pipeline.


Instructions:

   - Provide step-by-step instructions for Integrating Helm with Jenkins.

   - Simplify Jenkins configurations for Helm chart deployments. 