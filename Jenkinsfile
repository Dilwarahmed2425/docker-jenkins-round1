pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Dilwarahmed2425/docker-jenkins-round1'
            }
        }

        stage('Build Website Image') {
            steps {
                sh 'docker build -t website-app .'
            }
        }

        stage('Build API Image') {
            steps {
                sh 'docker build -t api-app ./api'
            }
        }

        stage('Run Containers') {
            steps {
                sh '''
                docker rm -f website-container || true
                docker rm -f api-container || true

                docker run -d --name website-container -p 8082:80 website-app
                docker run -d --name api-container -p 5000:5000 api-app
                '''
            }
        }
    }
}
