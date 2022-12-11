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
                emailext (
                    subject: "STARTED: Job '${env.JOB_NAME}'",
                    body: """<p>STARTED: Job '${env.JOB_NAME}':</p>
                    <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME}</a>&QUOT;</p>""",
                    recipientProviders: emailextrecipients([culprits(), requestor()])
                    )
                emailext (
                    body: 'Test Message',
                    subject: 'Test Subject',
                    to: 'daniel.lupu@ghimpe.ro')
                echo params.CHOICE
                sh '''
                echo 'w command' > ${export_file}
                w >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'who command' >> ${export_file}
                who >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'whoami command' >> ${export_file}
                whoami >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'pwd command' >> ${export_file}
                pwd >> ${export_file}
                echo '----------------------' >> ${export_file}
                echo 'ls -al command' >> ${export_file}
                ls -al >> ${export_file}
                echo '----------------------' >> ${export_file}
                '''
                archiveArtifacts artifacts: env.export_file, followSymlinks: false
            }
            post {
                always {
                    cleanWs()
                }
                success {
                    emailext (
                        subject: "SUCCESSFUL: Job '${env.JOB_NAME}'",
                        body: """<p>SUCCESSFUL: Job '${env.JOB_NAME}':</p>
                        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME}</a>&QUOT;</p>""",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                        )
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
