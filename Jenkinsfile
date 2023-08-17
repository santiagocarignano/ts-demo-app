pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                cd app && npm install
            }
        }
        stage('Test') {
            steps {
                cd app && npm test
            }
        }
        stage('Docker Build') {
            steps {
                cd app && docker build -t ts-demo-app .
            }
        }
        stage('Docker Build') {
            steps {
                aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 444106639146.dkr.ecr.us-east-1.amazonaws.com
                docker tag ts-demo-app:latest 444106639146.dkr.ecr.us-east-1.amazonaws.com/ts-demo-app:jenkins-${BUILD_NUMBER}
                docker push 444106639146.dkr.ecr.us-east-1.amazonaws.com/ts-demo-app:jenkins-${BUILD_NUMBER}
            }
        }
    }
}