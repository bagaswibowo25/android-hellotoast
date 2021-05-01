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
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit skipPublishingChecks: true 'test-results/*.xml'
                }
            }
        }
    }
}
