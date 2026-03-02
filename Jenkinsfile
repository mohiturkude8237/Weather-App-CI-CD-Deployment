pipeline {
    agent { label 'Vinod' }

    stages {

        stage('Clone Code') {
            steps {
                git url: 'https://github.com/mohiturkude8237/Weather-App-CI-CD-Deployment.git', branch: 'main'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t weather-app-prod .'
            }
        }

        stage('Deploy with Compose') {
            steps {
                sh '''
                  docker compose down || true
                  docker compose up -d
                '''
            }
        }

        stage('Smoke Test') {
            steps {
                sh 'sleep 5'
                sh 'curl -f http://localhost'
            }
        }
    }
}
