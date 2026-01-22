pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-demo-app"
        CONTAINER_NAME = "devops-demo-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Docker Version Check') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Stop Old Container (if exists)') {
            steps {
                bat '''
                docker stop %CONTAINER_NAME% || echo Container not running
                docker rm %CONTAINER_NAME% || echo Container not found
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker run -d ^
                --name %CONTAINER_NAME% ^
                -p 3000:3000 ^
                %IMAGE_NAME%
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build & Deployment Successful!'
        }
        failure {
            echo '❌ Build Failed! Check logs.'
        }
    }
}

