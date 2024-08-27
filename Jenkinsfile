pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
                // sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit and integration tests with Selenium'
                // sh 'mvn test'
                // sh 'mvn integration-test'
            }
            post {
                always {
                    emailext attachLog: true,
                        subject: "Test Stage Status: ${currentBuild.result}",
                        body: "The test stage has completed with status: ${currentBuild.result}",
                        to: 'anhthuw.aus2312@gmail.com'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube'
                // sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP'
                // sh 'zap-cli quick-scan --self-contained --start-options "-config api.disablekey=true" $TARGET_URL'
            }
            post {
                always {
                    emailext attachLog: true,
                        subject: "Security Scan Stage Status: ${currentBuild.result}",
                        body: "The security scan stage has completed with status: ${currentBuild.result}",
                        to: 'anhthuw.aus2312@gmail.com'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to AWS EC2 staging server'
                // sh 'ansible-playbook deploy-staging.yml'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging with Postman/Newman'
                // sh 'newman run postman_collection.json -e staging_environment.json'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to AWS EC2 production server'
                // sh 'ansible-playbook deploy-production.yml'
            }
        }
    }
}