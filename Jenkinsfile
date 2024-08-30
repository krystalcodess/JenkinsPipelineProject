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
                        def testLog = currentBuild.rawBuild.getLog(10000).join('\n')
                        writeFile file: 'test_log.txt', text: testLog
                        emailext attachmentsPattern: 'test_log.txt',
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
                        def securityLog = currentBuild.rawBuild.getLog(10000).join('\n')
                        writeFile file: 'security_log.txt', text: securityLog
                        emailext attachmentsPattern: 'security_log.txt',
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
            script {
                def jobUrl = env.BUILD_URL
                emailext subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                    body: """
                        Good news! The pipeline ${currentBuild.fullDisplayName} completed successfully.
                        
                        You can view the full log at: ${jobUrl}console
                    """,
                    to: 'anhthuw.aus2312@gmail.com'
            }
        }
        failure {
            script {
                def jobUrl = env.BUILD_URL
                emailext subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                    body: """
                        Oops! The pipeline ${currentBuild.fullDisplayName} failed.
                        
                        You can view the full log at: ${jobUrl}console
                    """,
                    to: 'anhthuw.aus2312@gmail.com'
            }
        }
    }
}
