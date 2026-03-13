pipeline {
    agent any

    environment {
        PROJECT_NAME = "disaster-management-mlops"
        COMPOSE_PROJECT = "disaster_v2"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Het1014/Disaster-Management-MLOps.git'
            }
        }

        stage('Verify Docker') {
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
                sh 'docker compose -p ${COMPOSE_PROJECT} up -d'
            }
        }

        stage('Check Running Containers') {
            steps {
                sh 'docker ps'
            }
        }

        stage('API Health Check') {
            steps {
                script {
                    sh '''
                    sleep 10
                    curl -f http://localhost:8000/health || exit 1
                    '''
                }
            }
        }

    }

    post {

        success {
            echo "Deployment Successful"
        }

        failure {
            echo "Pipeline Failed"
        }

        always {
            echo "Pipeline Completed"
        }

    }
}
