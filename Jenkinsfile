pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'app/build/libs/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }

        failure {
            echo 'Build or tests failed.'
        }
    }
}
