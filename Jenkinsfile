pipeline {
    agent {
        docker {
            image 'python:3.10'
        }
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Het-Buch/Disaster-Management-MLOps.git'
            }
        }

        stage('Check Project Structure') {
            steps {
                sh 'ls -R'
            }
        }

        stage('Install API Dependencies') {
            steps {
                sh 'pip install -r api/requirements.txt'
            }
        }

        stage('Install ML Dependencies') {
            steps {
                sh 'pip install -r ml/requirements.txt'
            }
        }

        stage('Install Streamlit Dependencies') {
            steps {
                sh 'pip install -r streamlit/requirements.txt'
            }
        }

        stage('Verify Python Environment') {
            steps {
                sh 'python --version'
                sh 'pip --version'
            }
        }

        stage('Check Streamlit Syntax') {
            steps {
                sh 'python -m py_compile streamlit/app.py'
            }
        }

    }
}
