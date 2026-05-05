pipeline {
    agent any

    environment {
        IMAGE_NAME = "cloudkart"
        CONTAINER_NAME = "cloudkart"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/cloudkart-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cloudkart ./backend'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f cloudkart || true'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d -p 5000:5000 \
                -e MONGO_URI="mongodb+srv://username:password@cluster.mongodb.net/cloudkart" \
                --name cloudkart cloudkart
                '''
            }
        }
    }
}