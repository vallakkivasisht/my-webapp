pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-webapp'
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {
        stage('Deploy to K3s') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}

