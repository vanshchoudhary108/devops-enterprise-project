pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker rm -f devops-container || exit 0
                docker run -d -p 8081:80 --name devops-container devops-app
                '''
            }
        }
    }
}

