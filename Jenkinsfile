pipeline {
    agent any
    
    triggers {
        pollSCM('*/5 * * * *')
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
        }

        stage('Unit Tests') {
            steps {
                gradlew('test')
            }
            post {
                always {
                    junit skipPublishingChecks: true, 'app/build/test-results/**/*.xml'
                }
            }
            post {
                failure {
                    mail to: 'ananda.dwirahmawati313@gmail.com', subject: 'Build failed', body: 'Please fix!'
                }
            }
        }
    }
}
