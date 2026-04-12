pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR-REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t signstream-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop app || true'
                sh 'docker rm app || true'
                sh 'docker run -d -p 3000:8080 --name app signstream-app'
            }
        }
    }
}
