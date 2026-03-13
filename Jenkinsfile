pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/Het-Buch/Disaster-Management-MLOps.git'
            }
        }

        stage('Cleanup Old Containers') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Build Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Start Services') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Check Containers') {
            steps {
                sh 'docker ps'
            }
        }
        stage('Show Running Containers') {
            steps {
                sh 'docker ps -a'
            }
        }
    }
}
