pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'

            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
        }
    }

    post {
        success {
            mail to: 'anhthuw.aus2312@gmail.com',
                 subject: "Pipeline Successful: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                 body: "The pipeline has completed successfully."
        }
        failure {
            mail to: 'anhthuw.aus2312@gmail.com',
                 subject: "Pipeline Failed: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                 body: "The pipeline has failed. Please check the logs."
        }
    }
}