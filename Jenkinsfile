pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t wrong-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop dj-round1-container || true
                docker rm dj-round1-container || true

                docker run -d -p 8082:80 \
                --name dj-round1-container \
                dj-round1-app
                '''
            }
        }
    }
}
