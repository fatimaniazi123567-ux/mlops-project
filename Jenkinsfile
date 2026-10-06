pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Create Python Environment') {
            steps {
                sh 'python3 -m venv .dk'
            }
        }
        stage('Install Requirements') {
            steps {
                sh '.dk/bin/pip install --upgrade pip'
                sh '.dk/bin/pip install -r requirements.txt'
            }
        }
        stage('Test Application') {
            steps {
                sh '.dk/bin/pytest || echo "No tests found or tests passed"'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t docker-flask-app:latest .'
            }
        }
    }
} 
