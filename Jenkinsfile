pipeline {
  agent any

  environment {
    IMAGE_NAME = 'my-webapp'
    KUBECONFIG = '/var/lib/jenkins/.kube/config'
  }

  stages {
    stage('Clone Repo') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t my-webapp:latest .'
      }
    }

    stage('Delete Existing Deployment') {
      steps {
        sh 'kubectl delete deployment my-webapp || true'
      }
    }

    stage('Deploy to K3s') {
      steps {
        sh 'kubectl apply -f k8s/deployment.yaml'
        sh 'kubectl apply -f k8s/service.yaml'
      }
    }
  }
}
