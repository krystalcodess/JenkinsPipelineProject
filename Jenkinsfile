pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project using Maven'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit'
            }
            post {
                success {
                    emailext subject: "[SIT223] Jenkins Pipeline: Unit and Integration Tests Stage - ${currentBuild.currentResult}",
                            body: "The Unit and Integration Tests stage has completed with status: ${currentBuild.currentResult}",
                            attachLog: true,
                            to: "anhthuw.aus2312@gmail.com"
                }
                failure {
                    emailext subject: "[SIT223] Jenkins Pipeline: Unit and Integration Tests Stage - ${currentBuild.currentResult}",
                            body: "The Unit and Integration tests failed. ${currentBuild.currentResult}",
                            attachLog: true,
                            to: "anhthuw.aus2312@gmail.com"
                }
                
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube in jenkins'
            }
        }
        
        stage('Security Scan') {
            steps {
                 echo 'Performing security scan with Snyk Code'
            }
            
            post {
                success {
                    emailext subject: "[SIT223] Jenkins Security Scan Notification - ${currentBuild.currentResult}",
                            body: "The Security Scan stage has completed with status: ${currentBuild.currentResult}.",
                            attachLog: true,
                            to: "anhthuw.aus2312@gmail.com"
                }
                failure {
                    emailext subject: "Jenkins Security Scan notification - ${currentBuild.currentResult}",
                            body: "Security Scan failed. ${currentBuild.currentResult}",
                            attachLog: true,
                            to: "anhthuw.aus2312@gmail.com"
                }
                
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to AWS EC2 Staging'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging using Maven'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to AWS EC2 Production'
            }
        }
    }

     
}
