pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/MADHU8912/cloudkart-app.git', credentialsId: 'github-creds'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cloudkart ./backend'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker rm -f cloudkart || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker run -d -p 5000:5000 ^
                -e MONGO_URI="mongodb+srv://username:password@cluster.mongodb.net/cloudkart" ^
                --name cloudkart cloudkart
                '''
            }
        }
    }
}