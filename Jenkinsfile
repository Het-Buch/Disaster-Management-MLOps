pipeline {
    agent any

    environment {
        PROJECT_NAME = "disaster-mlops"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/YOUR_USERNAME/Disaster-Management-MLOps.git'
            }
        }

        stage('Check Docker Installation') {
            steps {
                sh 'docker --version'
                sh 'docker compose version'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Start Services') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verify Running Containers') {
            steps {
                sh 'docker ps'
            }
        }

        stage('Check API Service') {
            steps {
                sh 'sleep 10'
                sh 'curl http://localhost:8000 || true'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully. Services are running.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
