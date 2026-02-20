pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Cloning repository...'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-app .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop jenkins-container || exit 0'
                bat 'docker rm jenkins-container || exit 0'
                bat 'docker run -d -p 3000:3000 --name jenkins-container jenkins-app'
            }
        }
    }
}