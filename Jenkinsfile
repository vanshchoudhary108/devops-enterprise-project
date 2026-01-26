pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t devops-web:v1 -f docker/Dockerfile .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f devops-web || true
                docker run -d -p 3000:3000 --name devops-web devops-web:v1
                '''
            }
        }
    }
}

