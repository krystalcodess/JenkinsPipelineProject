pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Replace with actual build command, e.g., 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                // Replace with actual test command, e.g., 'mvn test'
            }
            post {
                always {
                    script {
                        def testLog = sh(script: 'cat ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log', returnStdout: true).trim()
                        
                        mail to: 'anhthuw.aus2312@gmail.com',
                             subject: "Test Stage ${currentBuild.currentResult}: ${currentBuild.fullDisplayName}",
                             body: """
                                The Test stage has ${currentBuild.currentResult}.
                                
                                Log output:
                                ${testLog}
                             """
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                // Replace with actual code analysis tool command, e.g., 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Replace with actual security scan tool command, e.g., 'dependency-check'
            }
            post {
                always {
                    script {
                        def securityLog = sh(script: 'cat ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log', returnStdout: true).trim()
                        
                        mail to: 'anhthuw.aus2312@gmail.com',
                             subject: "Security Scan ${currentBuild.currentResult}: ${currentBuild.fullDisplayName}",
                             body: """
                                The Security Scan stage has ${currentBuild.currentResult}.
                                
                                Log output:
                                ${securityLog}
                             """
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Replace with deployment commands, e.g., 'scp' or 'ssh' commands
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Replace with staging environment test commands
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server AWS CLI'
                // Replace with production deployment commands
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            mail to: 'anhthuw.aus2312@gmail.com',
                 subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                 body: "Good news! The pipeline ${currentBuild.fullDisplayName} completed successfully."
        }
        failure {
            mail to: 'anhthuw.aus2312@gmail.com',
                 subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                 body: "Oops! The pipeline ${currentBuild.fullDisplayName} failed."
        }
    }
}
