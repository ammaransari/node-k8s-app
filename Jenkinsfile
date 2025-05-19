pipeline {
    agent any

    environment {
        IMAGE_NAME = 'node-k8s-app:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'eval $(minikube docker-env) && docker build -t $IMAGE_NAME .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl delete -f k8s/ || true'
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
