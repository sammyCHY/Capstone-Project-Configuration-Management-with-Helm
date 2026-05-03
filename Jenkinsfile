pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {
        stage('Deploy with Helm') {
            steps {
                sh 'helm upgrade --install my-webapp ./webapp --namespace default'
            }
        }
    }
}