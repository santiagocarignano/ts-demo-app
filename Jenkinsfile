pipeline {
    agent any
    stages {
        stage('print') {
            steps {
                sh 'echo "Hello World"'
            }
        }
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
                sh 'cd app && docker build -t  439355309749.dkr.ecr.us-east-1.amazonaws.com/app-jenkins-testing:jenkins-${BUILD_NUMBER} .'
            }
        }
        // stage('Docker Push') {
        //     steps {
        //         sh '''
        //             aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 444106639146.dkr.ecr.us-east-1.amazonaws.com
        //             docker push  444106639146.dkr.ecr.us-east-1.amazonaws.com/app:jenkins-${BUILD_NUMBER} 
        //           '''
        //     }
        // }
    }
}  