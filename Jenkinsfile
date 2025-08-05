pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-demo-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name nodejs-demo-app nodejs-demo-app'
            }
        }
    }
    post {
        always {
            sh 'docker rm -f nodejs-demo-app || true'
        }
    }
}
