pipeline {
    agent any

    environment {
        CLOUDINARY_API_SECRET = "FGQvs-WYhzHd76BMFVxP9C1BS2Y"
        CLOUDINARY_API_KEY = "532658782527543"
        CLOUDINARY_CLOUD_NAME = "dtd8jg6ps"
        JWT_SECRET= "dh7ap9IJOkGUef9l99IDFNRbyAKsctTNGxwU1cE12ee"
        MONGODB_STRING = "mongodb://mongo:27017"

    }

    stages {

        stage('Clone Repository') {
            steps {
                 git branch: 'main', url: 'https://github.com/sandhu02/signstream.git'
            }
        }

        stage('Build & Run with Docker Compose') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up --build -d'
            }
        }

    }
}
