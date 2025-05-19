pipeline {
  agent any

  environment {
    IMAGE_NAME = "node-k8s-app"
  }

  stages {
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Load image to Minikube') {
      steps {
        sh 'minikube image load $IMAGE_NAME'
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f k8s/'
      }
    }
  }
}
