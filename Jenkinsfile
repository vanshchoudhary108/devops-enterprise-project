pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/vanshchoudhary108/devops-enterprise-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-web:v1 -f docker/Dockerfile .'
            }
        }
    }
}

