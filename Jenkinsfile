```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-docker-devops .'
            }
        }

        stage('Test Docker Image') {
            steps {
                bat 'docker image inspect jenkins-docker-devops'
                echo 'Docker image built successfully'
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Great news! The Jenkins pipeline completed successfully.\n\nJob: ${env.JOB_NAME}\nBuild: #${env.BUILD_NUMBER}\nBuild URL: ${env.BUILD_URL}",
                to: 'nekuavasarama21@gmail.com'
            )
        }
        failure {
            emailext(
                subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins pipeline failed. Please check the console output.\n\nJob: ${env.JOB_NAME}\nBuild: #${env.BUILD_NUMBER}\nBuild URL: ${env.BUILD_URL}",
                to: 'nekuavasarama21@gmail.com'
            )
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
```
