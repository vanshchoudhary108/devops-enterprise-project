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
                sh 'docker build -t devops-web:v1 .'
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

