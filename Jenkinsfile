pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'osama8558/osama-auto-app'
    }

    stages {

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f osama-auto-container || true'
                sh 'docker run -d --name osama-auto-container -p 9092:80 $DOCKER_IMAGE'
            }
        }
    }
}
