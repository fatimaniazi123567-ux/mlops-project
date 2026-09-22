pipeline {
    agent any
    stages {
        stage('Build Image') {
            steps {
                sh 'docker build -t myimage .'
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker rm -f flask-app || true'
                sh 'docker run -d -p 5000:5000 --name flask-app myimage'
            }
        }
    }
}
