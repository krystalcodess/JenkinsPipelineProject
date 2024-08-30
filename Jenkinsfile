pipeline {
    agent any
    
    environment {
        EMAIL_RECIPIENT = 'anhthuw.aus2312@gmail.com'
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project using Maven...'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit...'
            }
            post {
                always {
                    script {
                        emailext subject: "Jenkins Pipeline: Unit and Integration Tests - ${currentBuild.currentResult}",
                                body: "The Unit and Integration Tests stage has completed with status: ${currentBuild.currentResult}.\n\nBuild URL: ${env.BUILD_URL}",
                                attachLog: true,
                                compressLog: true,
                                to: env.EMAIL_RECIPIENT
                    }
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube...'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with Snyk Code...'
                // Add actual Snyk scan command here, e.g.:
                // sh 'snyk test'
            }
            post {
                always {
                    script {
                        emailext subject: "Jenkins Pipeline: Security Scan - ${currentBuild.currentResult}",
                                body: "The Security Scan stage has completed with status: ${currentBuild.currentResult}.\n\nBuild URL: ${env.BUILD_URL}",
                                attachLog: true,
                                compressLog: true,
                                to: env.EMAIL_RECIPIENT
                    }
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to AWS EC2 Staging...'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging environment...'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to AWS EC2 Production...'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed.'
            emailext subject: "Jenkins Pipeline: Overall Build Failed - ${currentBuild.fullDisplayName}",
                    body: "The pipeline has failed. Please check the console output for details.\n\nBuild URL: ${env.BUILD_URL}",
                    attachLog: true,
                    compressLog: true,
                    to: env.EMAIL_RECIPIENT
        }
    }
}
