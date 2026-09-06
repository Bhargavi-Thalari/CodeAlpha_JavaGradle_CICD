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

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p deployed-app
                    cp app/build/libs/*.jar deployed-app/app.jar
                    echo "Application deployed successfully!"
                '''
            }
        }
    }

    post {
        success {
            echo 'Build, tests and deployment completed successfully!'
        }

        failure {
            echo 'Build, tests or deployment failed.'
        }
    }
}
