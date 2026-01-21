pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-web:v2 -f docker/Dockerfile .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f devops-web || true
                docker run -d -p 8090:80 --name devops-web devops-web:v2
                '''
            }
        }
    }
}

