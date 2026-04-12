pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Stop Old Part 2') {
            steps {
                sh 'docker-compose -f docker-compose-part2.yml down || true'
            }
        }

        stage('Start Part 2') {
            steps {
                sh 'docker-compose -f docker-compose-part2.yml up -d'
            }
        }

        stage('Verify Running') {
            steps {
                sh 'docker ps'
                sh 'curl -I http://localhost:6000 || true'
            }
        }
    }
}        }

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
