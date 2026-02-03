pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/<username>/<repo>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t demo-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop demo || true
                docker rm demo || true
                docker run -d --name demo -p 5000:5000 demo-app
                '''
            }
        }
    }
}
