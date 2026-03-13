pipeline {
    agent any

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

        stage('Install Python') {
            steps {
                sh '''
                apt-get update
                apt-get install -y python3 python3-pip
                '''
            }
        }

        stage('Install API Dependencies') {
            steps {
                sh 'pip3 install -r api/requirements.txt'
            }
        }

        stage('Install ML Dependencies') {
            steps {
                sh 'pip3 install -r ml/requirements.txt'
            }
        }

        stage('Install Streamlit Dependencies') {
            steps {
                sh 'pip3 install -r streamlit/requirements.txt'
            }
        }

        stage('Verify Python Setup') {
            steps {
                sh 'python3 --version'
                sh 'pip3 --version'
            }
        }

        stage('Check Streamlit App Syntax') {
            steps {
                sh 'python3 -m py_compile streamlit/app.py || true'
            }
        }

    }
}
