pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
                sh '''
                rm -f some.txt
                w > some.txt
                who >> some.text
                whoami >> some.text
                pwd >> some.text
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
