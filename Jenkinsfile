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

        stage('Prepare Env File') {
            steps {
                sh 'cp /home/ubuntu/myapp/.env .env'
                sh 'ls -la'
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
}
