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