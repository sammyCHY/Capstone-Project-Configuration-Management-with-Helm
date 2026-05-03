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

   - Helm Charts: are packaged templates used to define, install, and manage applications on **Kubernetes**.

   - Kubernetes is the operating system for containers.
   - Helm is the package manager
   - Helm chart is the installed package.
   - Kubernetes uses helm charts.

2. Walkthrough of creating a basic Helm chart for a web application.

   - In this case I will have to create a Helm chart that deploys a simple web app to Kubernetes using Helm.

   - Before then, I have to create webapp first by using this command.
    
    `helm create webapp`

    ![The Image here shows helm creating webapp](image/helm-create-webapp.png)

    When you run `helm create webapp` It will automatically generates a "Helm chart". you will see all these below.

    ```
         webapp/
   ├── Chart.yaml
   ├── values.yaml
   ├── charts/
   └── templates/
   ```
   Above are the created chart.

    Then, the next is `helm install my-webapp ./webapp`

   Before all these installation above, then, ensure Kubernetes and helm has to be installed in the server.
   For helm installation in the server "Linux/Ubuntu" then, run this command: 
   
   ```
   curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
   ```
   ![The Image shows helm installation in the server](image/helm-installation.png)

   ![The Image shows helm version installation](image/helm-version.png)

   After the helm installation on the server the next is Kubernetes Cluster deployment on the Jenkins server, however, k3s or EKS can be used.
   In this particular project I want to deploy k3s cluster.
   Run this command below:

   ```
   curl -sfL https://get.k3s.io | sh -
   ```
   ![The Image shows the installation of kubernetes K3s Cluster](image/kubernetes-k3s-cluster.png)

   check the k3s cluster installation

   ```
   sudo kubectl get nodes
   ```

   ![The images shows k3s kubernetes cluster nodes](image/kubectl-get-nodes.png)

Remember In this project you need some pre-requisite to be installed in the `Jenkins server` like:

   - K3s Kubernetes cluster or EKS
   - Helm.
   - Git

To Install Git run this command: `sudo apt install git -y`
   git --version.
Jenkins needs Git to pull my code from GitHub.
![The Image shows the git installation](image/git.png)

   ### Some Tips:
   - `Install` ----> deploy
   - `my-webapp` ---> released name
   - `./webapp` ---> chart folder

3. Cover Helm chart templating basics.


Instructions:

   - Provide beginner-friendly explanations of Helm chart concepts.

   **Step by step detailed explanation.**
1. A Helm chart is simply a packaged set of instruction for deploying an application to Kubernetes, in a layman explanation, think of it like a recipe. If Kubernetes is the Kitchen, then: 

   - Kubernetes = the Kitchen
   - Helm = the chef
   - Helm chart = the recipe.

The recipe tells the chef:
   - What ingredients to use.
   - How much of it.
   - How to prepare it.
Without Helm, deploying an app to Kubernetes means writing many separate YAML files. eg..., 
      deployment.yaml
      service.yaml
      configmap.yaml
      ingress.yaml
      secret.yaml
That gets messy quickly,Helm allows you to bundle everything into one organized package. Instead of manually applying many files: 


   - Include a hands-on guide for creating a simple Helm chart.
When you run helm create webapp in your directory, It will automatically create `helm charts`.

### Working with Helm Charts 

**Objective:** Guide students in working with Helm charts for application deployment.

At this point I have my Kubernetes cluster K3s installed on my aws instance server, therefore, 
If I run `helm install my-webapp ./webapp` on my local working directory, It will fail.

Now I have to access aws instance via ssh, then run this command:
`sudo cat /etc/rancher/k3s/k3s.yaml` to see the `YAML` file.

![The Image shows the K3S.YAML of the kube cluster](image/k3s-cluster.png)

Inside the YAML file you will see `server: https://127.0.0.1:6443` then change it to `server: https://3.94.89.183:6443` this matters because the config was generated for local access on the server itself.

The reason for this is that the first server: `https://127.0.0.1:6443` works only on the AWS server itself, because `127.0.0.1` means: "connect to this same machine" therefore If you SSH into your AWS instance and run `kubectl get nodes` then `127.0.0.1:6443` correctly points to the K3S API running locally on the server. But when you copy that kubeconfig to your Windows laptop and run: `helm install ...` the local computer interprets: server: `https://127.0.0.1:6443` as connect the Kubernetes running on my ***laptop*** which does not exist, that's the main reason Helm was trying localhost and failing. So change it to :`server: https://3.94.89.183:6443` because I'm telling my local machine: to Connect to the Kubernetes API server running on my AWS instance at this Public IP.

Now If you want to edit the `k3s.yaml` file then, you have to copy it to somewhere you can edit. On the AWS server follow this steps and run this command one by one.

1. Copy the file into your home folder.
   `sudo cp /etc/rancher/k3s/k3s.yaml /home/ubuntu/k3s.yaml`

2. Give yourself ownership.
   `sudo chown ubuntu:ubuntu /home/ubuntu/k3s.yaml`

3. Open it for editing.
   `nano /home/ubuntu/k3s.yaml`

Now you will actually see the file contents then change the recommended server `https`. Note: make sure you change to the current public IP running ant that moment because It changes.

   ![The Image shows the edited k3s cluster file ](image/k3s-yaml-file-edit1.png)

   ![The Image shows the edited k3s cluster file ](image/k3s-yaml-file-edit2.png)

4. Copy file from AWS ---> To my local computer. Run this command:
      `scp -i your-key.pem ubuntu@3.94.89.183:/home/ubuntu/k3s.yaml ~/.kube/config`  . Make sure the IP is your current public IP running on your server because it changes. and pay attention to the directory you run the command, It must be in the place the `.pem `key is saved to.
![The Image shows the copying of the file from AWS to laptop](image/k3s-kubeconfig.png)

This is another experience after performing the task showing in the Image above, I want to `kubectl get nodes` on my local computer to confirm the connection then *error* on the Image below displayed.

![The Image shows the displayed error](image/kubectl-get-error-nodes.png). when you see something like this, you have to go to the AWS--->Security-group and edit the inbound rule to add a port range.

![The Image shows the adding of Port range](image/add-port-rule.png)

After this process, It failed again. Below is the error I got.

`Documents/project_data/Capstone-Project-Configuration-Management-with-Helm (main) $ kubectl get nodes E0502 20:50:25.963584 12040 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://35.168.17.239:6443/api?timeout=32s\": tls: failed to verify certificate: x509: certificate is valid for 10.43.0.1, 127.0.0.1, 172.31.41.144, ::1, not 35.168.17.239" E0502 20:50:26.195127 12040 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://35.168.17.239:6443/api?timeout=32s\": tls: failed to verify certificate: x509: certificate is valid for 10.43.0.1, 127.0.0.1, 172.31.41.144, ::1, not 35.168.17.239" E0502 20:50:26.419590 12040 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://35.168.17.239:6443/api?timeout=32s\": tls: failed to verify certificate: x509: certificate is valid for 10.43.0.1, 127.0.0.1, 172.31.41.144, ::1, not 35.168.17.239" E0502 20:50:26.642499 12040 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://35.168.17.239:6443/api?timeout=32s\": tls: failed to verify certificate: x509: certificate is valid for 10.43.0.1, 127.0.0.1, 172.31.41.144, ::1, not 35.168.17.239" E0502 20:50:26.854805 12040 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://35.168.17.239:6443/api?timeout=32s\": tls: failed to verify certificate: x509: certificate is valid for 10.43.0.1, 127.0.0.1, 172.31.41.144, ::1, not 35.168.17.239" Unable to connect to the server: tls: failed to verify certificate: x509: certificate is valid for 10.43.0.1, 127.0.0.1, 172.31.41.144, ::1, not 35.168.17.239`

The error means that My Kubernetes API Server certificate was created for these addresses:

   - 127.0.0.1 (localhost)
   - 172.31.41.144 (Private AWS IP)
   - 10.43.0.1 (Cluster internal IP)

   But NOT:
   - 35.168.17.239 (my Public IP). Therefore, kubectl is rejecting the connection because TLS security is strict.

Now to fix it, I must reconfigure K3S with correct IP.

Run this command on the server: `sudo nano /etc/systemd/system/k3s.service`

`Find ExecStart and modify/add: --tls-san 35.168.17.239`

```
ExecStart=/usr/local/bin/k3s server \
  --tls-san 35.168.17.239
```

![The Image shows the reconfigure of k3s cluster](image/k3s-reconfigure.png)

Then exit the nano file and restart k3s.

```
sudo systemctl daemon-reload
sudo systemctl restart k3s
```
![The Image shows the k3s start, reload-daemon again](image/k3s-start-reload-daemon.png)

![The Image shows the k3s status](image/k3s-status.png)

- Copy Kubeconfig again

```
sudo cp /etc/rancher/k3s/k3s.yaml /home/ubuntu/k3s.yaml
sudo chown ubuntu:ubuntu /home/ubuntu/k3s.yaml
```
Then, Edit.

`nano /home/ubuntu/k3s.yaml`

Ensure:
`server: https://35.168.17.239:6443` the public server IP is added on the nano nano k3s.yaml file.

- Download to your laptop
From Windows: make sure you are the right directory where your secret key is stored, in my case, I have my `.pem` key in my downloads, therefore, I have to cd into the download to run this command below:
`scp -i baby.pem ubuntu@35.168.17.239:/home/ubuntu/k3s.yaml ~/.kube/config`
![The Image shows the kubeconfig download](image/kubeconfig-download0.png)
![The Image shows the kubeconfig download](image/kubeconfig-download.png)

After all these process, I to cd to the local working directory and run `kubectl get nodes` below is the image output.

![the Image shows the nodes installed and can be accessed my local working directory](image/kubectl-get-nodes-local.png)

After that I can now install my-webapp ./webapp on my working directory.

![The Image shows the deployment of my-webapp in my current working directory](image/helm-install-myweb-app.png)

   
**Steps:**

1.  Deploy a sample web application using the Helm chart created.

![This Image show that the helm chart was used to deploy a simple web app to the k3s cluster](image/helm-install-myweb-app.png)

![The apps is running](image/kubectl-get-pods.png)
![The kubectl get svc](image/kubectl-get-svc.png)

2. Introduce values and templates in Helm Charts.

3. Explore upgrading and rolling back applications using Helm.


## Instructions:

- Include simple examples and explanations for deploying applications with Helm.

- Provide a guide for Helm chart customization.


### Integrating Helm with Jenkins.

**Objective: Integrate Helm with Jenkins for automated deployments.

### Steps:

1. Integrate Jenkins with Helm for deployment.
   - Create Jenkinsfile in the root repository.

```
   pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/sammyCHY/Capstone-Project-Configuration-Management-with-Helm.git'
            }
        }

        stage('Deploy with Helm') {
            steps {
                sh 'helm upgrade --install my-webapp ./webapp --namespace default'
            }
        }
    }
}
```

2. Configure Jenkins to use Helm charts in the CI/CD Pipeline.

   ### Create Jenkins Pipeline Job and configure it. In Jenkins:

   - New Item
   - Enter name: `helm-pipeline`
   - Select Pipeline
   - OK.

![The Image shows the Helm-Pipeline created](image/helm-pipeline-created.png)

### Pipeline Configured: Under Pipeline

   - Definition ---> Pipeline script from SCM
   - SCM ---> Git
   - Repository URL ---> Your GitHub Repo
   - Branch ---> `*/main` 
   - Script Path ---> `Jenkinsfile`
SAVE. 
   Jenkins will read Jenkinsfile from GitHub.
![The Image shows Jenkins Configure](image/helm-pipeline-configured1.png)
![The Image shows Jenkins Configure](image/helm-pipeline-configured2.png)
![The Image shows Jenkins Configure](image/helm-pipeline-configured3.png)
![The Image shows Jenkins Configure](image/helm-pipeline-configured4.png)


After this I need to activate a controlled Github webhook with jenkins url.
 ![The Image shows github webhook activated with jenkins](image/github-webhook.png)
 ![The Image shows github webhook activated with jenkins](image/github-webhook1.png)
 ![The Image shows github webhook activated with jenkins](image/github-webhook2.png)
Instructions:

   - Provide step-by-step instructions for Integrating Helm with Jenkins.

   - Simplify Jenkins configurations for Helm chart deployments. 