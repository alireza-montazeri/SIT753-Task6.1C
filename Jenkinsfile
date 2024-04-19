pipeline {
    agent any
    environment {\
        EMAIL_RECIPIENT = 's223632922@deakin.edu.au'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the project using Maven.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit and Mockito.'
            }
            post {
                success {
                    script {
                        def log = currentBuild.rawBuild.getLog(100).join('\n') // Get the last 100 lines of the console log
                        emailext (
                            subject: "SUCCESS: Unit and Integration Tests",
                            body: "The Unit and Integration Tests stage completed successfully.\\n\\nConsole Log:\\n${log}",
                            to: env.EMAIL_RECIPIENT
                        )
                    }
                }
                failure {
                    script {
                        def log = currentBuild.rawBuild.getLog(100).join('\n') // Get the last 100 lines of the console log
                        emailext (
                            subject: "FAILURE: Unit and Integration Tests",
                            body: "The Unit and Integration Tests stage failed.\\n\\nConsole Log:\\n${log}",
                            to: env.EMAIL_RECIPIENT
                        )
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube to ensure quality and standards.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing a security scan using OWASP ZAP to detect vulnerabilities.'
            }
            post {
                success {
                    script {
                        def log = currentBuild.rawBuild.getLog(100).join('\n')
                        emailext (
                            subject: "SUCCESS: Security Scan",
                            body: "The Security Scan stage completed successfully.\\n\\nConsole Log:\\n${log}",
                            to: env.EMAIL_RECIPIENT
                        )
                    }
                }
                failure {
                    script {
                        def log = currentBuild.rawBuild.getLog(100).join('\n')
                        emailext (
                            subject: "FAILURE: Security Scan",
                            body: "The Security Scan stage failed.\\n\\nConsole Log:\\n${log}",
                            to: env.EMAIL_RECIPIENT
                        )
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to a staging environment on AWS EC2.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Conducting integration tests in the staging environment using Selenium.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to the production server, also on AWS EC2.'
            }
        }
    }
}
