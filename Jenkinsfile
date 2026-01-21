pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'devops-web:v1'
        DOCKER_CONTAINER = 'devops-web'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vanshchoudhary108/devops-enterprise-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE -f docker/Dockerfile .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f $DOCKER_CONTAINER || true
                docker run -d -p 8081:80 --name $DOCKER_CONTAINER $DOCKER_IMAGE
                '''
            }
        }
    }
}

