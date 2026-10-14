
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
            echo 'SUCCESS: CI/CD pipeline completed!'
        }
        failure {
            echo 'FAILURE: Check the Jenkins console output.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
