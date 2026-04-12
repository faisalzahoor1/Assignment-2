pipeline {
    agent any

    triggers {
        githubPush()
    }

    environment {
        CLOUDINARY_API_SECRET = "FGQvs-WYhzHd76BMFVxP9C1BS2Y"
        CLOUDINARY_API_KEY = "532658782527543"
        CLOUDINARY_CLOUD_NAME = "dtd8jg6ps"
        JWT_SECRET = "dh7ap9IJOkGUef9l99IDFNRbyAKsctTNGxwU1cE12ee"
        MONGODB_STRING = "mongodb://mongo:27017"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Cleanup Old Containers') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Build & Run Containers') {
            steps {
                sh 'docker compose up --build -d'
            }
        }

        stage('Verify Running') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
