pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "devops-web:v1"
        DOCKER_CONTAINER = "devops-web"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                  docker build -t devops-web:v1 -f docker/Dockerfile .
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker rm -f devops-web || true
                  docker run -d -p 8081:80 --name devops-web devops-web:v1
                '''
            }
        }
    }
}

