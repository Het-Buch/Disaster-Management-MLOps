pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Het-Buch/Disaster-Management-MLOps.git'
            }
        }

        stage('Check Project Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt || true'
                sh 'pip install streamlit'
            }
        }

        stage('Run Streamlit App') {
            steps {
                sh 'streamlit run streamlit_app.py --server.port 8501 &'
                sh 'sleep 10'
            }
        }

        stage('Verify App Running') {
            steps {
                sh 'curl http://localhost:8501 || true'
            }
        }

    }
}
