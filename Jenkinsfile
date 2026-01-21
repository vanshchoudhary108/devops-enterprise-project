pipeline {
    agent { label 'docker-enabled' }  // Use a specific agent with Docker

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
                script {
                    // Add try-catch for debugging
                    try {
                        sh 'docker build -t $DOCKER_IMAGE -f docker/Dockerfile .'
                    } catch (Exception e) {
                        echo "Build failed: ${e.message}"
                        throw e
                    }
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    try {
                        sh '''
                        docker rm -f $DOCKER_CONTAINER || true
                        docker run -d -p 8081:80 --name $DOCKER_CONTAINER $DOCKER_IMAGE
                        '''
                        // Optional: Verify deployment
                        sh 'docker ps | grep $DOCKER_CONTAINER'
                    } catch (Exception e) {
                        echo "Deploy failed: ${e.message}"
                        throw e
                    }
                }
            }
        }
    }

    post {
        always {
            // Cleanup: Stop and remove container on failure
            sh 'docker rm -f $DOCKER_CONTAINER || true'
        }
    }
}
