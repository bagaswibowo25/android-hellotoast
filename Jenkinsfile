pipeline {
    agent any
    
    triggers {
        pollSCM('*/1 * * * *')
    }

    stages {
        stage('Pull') {
            steps {
                git 'https://github.com/misskecupbung/android-hellotoast.git'
            }
        }

        stage('Build') {
            steps {
                sh "gradle clean build"
            }
            post {
                failure {
                    mail to: 'ananda.dwirahmawati313@gmail.com', subject: 'Build failed', body: 'Please fix!'
                }
            }
        }
    }
}
