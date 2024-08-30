pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'anhthuw.aus2312@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building Code..."
                sleep 5
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests"
                sleep 5
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENT,
                        subject: "Unit and Integration Tests - ${currentBuild.currentResult}",
                        body: "Unit and Integration Tests have ${currentBuild.currentResult}.",
                        attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Performing code analysis"
                sleep 5
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan"
                sleep 5
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENT,
                        subject: "Security Scan - ${currentBuild.currentResult}",
                        body: "Security Scan has ${currentBuild.currentResult}.",
                        attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging"
                sleep 5
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging"
                sleep 5
            }
            post {
                always {
                    emailext to: env.EMAIL_RECIPIENT,
                        subject: "Staging Tests - ${currentBuild.currentResult}",
                        body: "Integration Tests on Staging have ${currentBuild.currentResult}.",
                        attachLog: true
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production"
                sleep 5
            }
        }
    }
}
