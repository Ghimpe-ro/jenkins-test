pipeline {
    agent any
    parameters{
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')    
        }
        environment{
            export_file = "some.txt"

        }

    stages {
        stage('stage 1') {
            when { expression { return params.TOGGLE } }
            options {
                timeout(time: 10, unit: 'MINUTES') 
            }
            steps {
                sh '''
                echo ${export_file}
                echo 'remove old file'
                rm -f ${export_file}
                echo 'w'
                w > ${export_file}
                echo 'who'
                who >> ${export_file}
                echo 'whoami'
                whoami >> ${export_file}
                echo 'pwd'
                pwd >> ${export_file}
                echo 'ls -al'
                ls -al
                '''
                archiveArtifacts artifacts: env.export_file, followSymlinks: false
            }
        }
        stage('stage 2') {
            steps {
                echo 'pwd'
                sh 'pwd'
                echo 'ls -al'
                sh 'ls -al'
            }
        }
    }
}
