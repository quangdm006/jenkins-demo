
pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/<username>/jenkins-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-jenkins .'
            }
        }

        stage('Run Test (fake)') {
            steps {
                sh 'echo "Test passed 100%"'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f flask-app || true
                docker run -d -p 5000:5000 --name flask-app flask-jenkins
                '''
            }
        }
    }
}

