pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sammyCHY/Capstone-Project-Configuration-Management-with-Helm.git'
            }
        }

        stage('Deploy with Helm') {
            steps {
                sh 'helm upgrade --install my-webapp ./webapp --namespace default'
            }
        }
    }
}