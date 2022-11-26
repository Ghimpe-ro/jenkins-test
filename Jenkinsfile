pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
                sh '''
                w > some.txt
                who >> some.text
                whoami >> some.text
                pwd >> some.text
                sudo docker ps
                '''
                archiveArtifacts artifacts: 'some.text', followSymlinks: false
            }
        }
        stage('stage 2') {
            steps {
                sh 'pwd'
                sh 'ls -al'
            }
        }
    }
}
