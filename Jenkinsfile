pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compile and package the source code using Maven.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Run unit tests with JUnit and integration tests with TestNG.'
            }
            post {
                success {
                    mail to: "ilikebeans53@gmail.com",
                        subject: "Build Successful - Unit and Integration Tests",
                        body: "Build was successful!",
                        attachLog: true  // This will attach the console log to the email
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyze the source code with SonarQube to detect bugs, code smells, and maintainability issues.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Scan the codebase for security vulnerabilities using OWASP ZAP.'
            }
            post {
                success {
                    mail to: "ilikebeans53@gmail.com",
                        subject: "Build Successful - Security Scan",
                        body: "Build was successful!",
                        attachLog: true  // This will attach the console log to the email
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploy the application to staging using Docker and AWS EC2 instances.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Execute integration tests in the staging environment using Selenium.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploy the application to production using Jenkins automation on AWS EC2 instances.'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up after pipeline execution.'
        }
    }
}
