pipeline {
    agent any

    stages {
        stage('Verify Environment') {
            steps {
                sh 'whoami'
                sh 'pwd'
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-web-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop my-web-app-container || true'
                sh 'docker rm my-web-app-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name my-web-app-container -p 8090:80 my-web-app'
            }
        }
    }
}
