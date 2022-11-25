pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
                sh '''cat >> some.text << \'END\'
                some stuff here
                more stuff
                END'''
                sh '''
                who >> some.text
                pwd >> some.text
                ip address >> some.text
                '''
                archiveArtifacts artifacts: 'some.text', followSymlinks: false
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
