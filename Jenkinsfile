pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t osama8558/osama-auto-app .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push osama8558/osama-auto-app'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f osama-auto-container || true'
                sh 'docker run -d --name osama-auto-container -p 9092:80 osama8558/osama-auto-app'
            }
        }
    }
}
