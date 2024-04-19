pipeline {
    agent any

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
    post {
        always {
            mail bcc: '', body: "A Jenkins build status email.\n\nBUILD: ${env.JOB_NAME}\nBUILD NUMBER: ${env.BUILD_NUMBER}\nBUILD STATUS: ${currentBuild.currentResult}", cc: '', from: '', replyTo: '', subject: "Build Status: ${currentBuild.currentResult}", to: "amontazeri8@gmail.com"
        }
    }
}

