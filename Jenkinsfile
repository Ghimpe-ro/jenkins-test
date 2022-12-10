pipeline {
    agent any
    parameters{
        // string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        // text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
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
                echo params.CHOICE
                sh '''
                echo ${export_file}
                echo 'w' > ${export_file}
                w >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'who' >> ${export_file}
                who >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'whoami' >> ${export_file}
                whoami >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'pwd' >> ${export_file}
                pwd >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'ls -al' >> ${export_file}
                ls -al ${export_file}
                ls -al
                '''
                archiveArtifacts artifacts: env.export_file, followSymlinks: false
            }
            post {
                always {
                    cleanWs()
                }
            }
        }
        stage('stage 2') {
            options {
                timeout(time: 10, unit: 'MINUTES') 
            }
            steps {
                echo params.CHOICE
                echo 'pwd'
                sh 'pwd'
                echo 'ls -al'
                sh 'ls -al'
            }
        }        
    }
}
