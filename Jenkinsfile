pipeline {
    agent { label '' }

    environment {
        IMAGE_NAME = "harish/fullstack-app"
    }

    stages {

        stage('Clone Code') {
            steps {
                echo "Cloning repository..."
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f fullstack-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                  -p 9000:8000 \
                  --name fullstack-app \
                  $IMAGE_NAME:latest
                '''
            }
        }
    }
}
