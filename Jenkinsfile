Jenkinsfile
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven (Build automation tool)."
                echo 'Tool: Maven'
            }
            post {
                always { 
                    mail to: "m.rovacsek@hotmail.com",
                    subject: "Build status email",
                    body: "The build has completed. Please check the logs for more details."
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using JUnit and integration tests with Selenium (Test automation tools)."
                echo 'Tool: JUnit (for Unit Tests) and TestNG (for Integration Tests)'
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code using SonarQube (Code analysis tool)."
                echo 'Tool: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan using OWASP Dependency-Check (Security scan tool)."
                echo 'Tool: OWASP Dependency-Check'
            }
            post {
                success {
                    mail to: "m.rovacsek@hotmail.com",
                    subject: "Security Scan Success",
                    body: "Security scan completed successfully."
                }
                failure {
                    mail to: "m.rovacsek@hotmail.com",
                    subject: "Security Scan Failure",
                    body: "Security scan failed. Please check the logs."
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a staging server (AWS EC2 instance)."
                echo 'Tool: AWS CLI'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment to ensure the application functions as expected in a production-like environment."
                echo 'Tool: Selenium (for web-based testing) or Postman (for API testing)'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to a production server (AWS EC2 instance)."
                echo 'Tool: AWS CLI'
            }
        }
    }
    post {
        success {
            mail to: "m.rovacsek@hotmail.com",
            subject: "Pipeline Success",
            body: "Pipeline completed successfully."
        }
        failure {
            mail to: "m.rovacsek@hotmail.com",
            subject: "Pipeline Failure",
            body: "Pipeline failed. Please check the logs."
        }
    }
}
