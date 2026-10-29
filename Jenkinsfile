
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t mywebapp .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f mywebapp-container || true'
                sh 'docker run -d --name mywebapp-container -p 8081:80 mywebapp'
            }
        }

        stage('Test') {
            steps {
                sh 'curl -f http://localhost:8081'
            }
        }
    }
}
