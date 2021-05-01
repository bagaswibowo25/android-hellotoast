pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/misskecupbung/android-hellotoast.git'

                // Run gradle project
                sh "gradle clean build"
            }

            post {
                // Testing using jUnit
                success {
                    junit skipPublishingChecks: true, testResults: 'test-results/*.xml'
                }
            }
        }
    }
}
