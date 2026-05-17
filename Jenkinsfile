pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t osama-auto-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f osama-auto-container || true'
                sh 'docker run -d --name osama-auto-container -p 9090:80 osama-auto-app'
            }
        }

    }
}
