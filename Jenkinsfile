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
                        def jobName = env.JOB_NAME
                        def buildNumber = env.BUILD_NUMBER
                        def logFile = "${jobName}-${buildNumber}-test.log"
                        
                        // Copy the log file
                        sh "cp \$JENKINS_HOME/jobs/${jobName}/builds/${buildNumber}/log ${logFile}"
                        
                        // Send email with attachment
                        emailext attachmentsPattern: "${logFile}",
                                 subject: "Test Stage Results: ${currentBuild.fullDisplayName}",
                                 body: "Please find attached the logs for the Test stage of ${currentBuild.fullDisplayName}.",
                                 to: 'anhthuw.aus2312@gmail.com'
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
                        def jobName = env.JOB_NAME
                        def buildNumber = env.BUILD_NUMBER
                        def logFile = "${jobName}-${buildNumber}-security.log"
                        
                        // Copy the log file
                        sh "cp \$JENKINS_HOME/jobs/${jobName}/builds/${buildNumber}/log ${logFile}"
                        
                        // Send email with attachment
                        emailext attachmentsPattern: "${logFile}",
                                 subject: "Security Scan Results: ${currentBuild.fullDisplayName}",
                                 body: "Please find attached the logs for the Security Scan stage of ${currentBuild.fullDisplayName}.",
                                 to: 'anhthuw.aus2312@gmail.com'
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
