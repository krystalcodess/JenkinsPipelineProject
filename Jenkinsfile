pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...(Updated)'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
            // Highlight start
            post {
                always {
                    emailext subject: "Test Stage Status: ${currentBuild.result}",
                             body: "The test stage has completed with status: ${currentBuild.result}",
                             to: "anhthuw.aus2312@gmail.com",
                             attachLog: true
                }
            }
            // Highlight end
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
            // Highlight start
            post {
                always {
                    emailext subject: "Security Scan Status: ${currentBuild.result}",
                             body: "The security scan stage has completed with status: ${currentBuild.result}",
                             to: "anhthuw.aus2312@gmail.com",
                             attachLog: true
                }
            }
            // Highlight end
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
    
    // Highlight start
    post {
        success {
            emailext subject: "Pipeline Success",
                      body: "The pipeline has completed successfully.",
                      to: "anhthuw.aus2312@gmail.com",
                      attachLog: true
        }
        failure {
            emailext subject: "Pipeline Failure",
                      body: "The pipeline has failed. Please check the logs.",
                      to: "anhthuw.aus2312@gmail.com",
                      attachLog: true
        }
    }
    // Highlight end
}
