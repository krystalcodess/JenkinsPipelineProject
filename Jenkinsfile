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
                        def logContent = Jenkins.instance.getItem(env.JOB_NAME).getBuildByNumber(env.BUILD_NUMBER).getLog(1000)
                        writeFile file: 'test_logs.txt', text: logContent.join('\n')
                        
                        mail to: 'anhthuw.aus2312@gmail.com',
                             subject: "Test Stage Completed: ${currentBuild.fullDisplayName}",
                             body: "The Test stage has completed. Please find the logs attached.",
                             attachmentsPattern: 'test_logs.txt'
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
                        def logContent = Jenkins.instance.getItem(env.JOB_NAME).getBuildByNumber(env.BUILD_NUMBER).getLog(1000)
                        writeFile file: 'security_scan_logs.txt', text: logContent.join('\n')
                        
                        mail to: 'anhthuw.aus2312@gmail.com',
                             subject: "Security Scan Completed: ${currentBuild.fullDisplayName}",
                             body: "The Security Scan stage has completed. Please find the logs attached.",
                             attachmentsPattern: 'security_scan_logs.txt'
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
                mail to: 'anhthuw.aus2312@gmail.com',
                     subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                     body: """
                        Good news! The pipeline ${currentBuild.fullDisplayName} completed successfully.
                        
                        You can view the full log at: ${jobUrl}console
                     """
            }
        }
        failure {
            script {
                def jobUrl = env.BUILD_URL
                mail to: 'anhthuw.aus2312@gmail.com',
                     subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                     body: """
                        Oops! The pipeline ${currentBuild.fullDisplayName} failed.
                        
                        You can view the full log at: ${jobUrl}console
                     """
            }
        }
    }
}
