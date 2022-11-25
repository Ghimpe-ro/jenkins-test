pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
                sh '''who
                pwd
                ip address
                '''
            }
        }
        stage('stage 2') {
            steps {
                sh 'whoami'
                sh 'pwd'
                sh 'ls -al'
            }
        }
    }
}
