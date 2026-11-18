pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-devops-app .'
            }
        }

        stage('Deploy Website') {
            steps {
                sh 'docker rm -f mywebsite || true'
                sh 'docker run -d --name mywebsite -p 8081:80 my-devops-app'
            }
        }

        stage('Test Website') {
            steps {
                sh 'docker exec mywebsite wget -qO- http://localhost'
            }
        }
    }
}
