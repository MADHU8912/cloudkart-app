pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/cloudkart-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cloudkart .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop cloudkart || true
                docker rm cloudkart || true
                docker run -d -p 5000:5000 --name cloudkart cloudkart
                '''
            }
        }
    }
}