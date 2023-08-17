pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'cd app && npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'cd app && npm test'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'cd app && docker build -t ts-demo-app .'
            }
        }
        stage('Docker Build') {
            steps {
                sh '''
                    cd app
                    docker build -t ts-demo-app .
                    docker tag ts-demo-app:latest 444106639146.dkr.ecr.us-east-1.amazonaws.com/ts-demo-app:jenkins-${BUILD_NUMBER}
                    docker push 444106639146.dkr.ecr.us-east-1.amazonaws.com/ts-demo-app:jenkins-${BUILD_NUMBER} 
                  '''
            }
        }
    }
}