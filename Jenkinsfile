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
            export_file = "some_1.txt"

        }

    stages {
        stage('stage 1') {
            when { expression { return params.TOGGLE } }
            options {
                timeout(time: 1, unit: 'HOURS') 
            }
            steps {
                sh '''
                rm -f ${export_file}
                w > ${export_file}
                who >> ${export_file}
                whoami >> ${export_file}
                pwd >> ${export_file}
                '''
                archiveArtifacts artifacts: ${export_file}, followSymlinks: false
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
