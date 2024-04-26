pipeline {
    agent any  // Specifies that the pipeline can run on any available agent

    environment {
        // Define any global environment variables here, like the recipient email
        EMAIL_RECIPIENT = 'ilikebeans53@gmail.com'
    }

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
                    emailext (
                        subject: "SUCCESS: Unit and Integration Tests Completed",
                        body: "Unit and Integration Tests completed successfully. See attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        subject: "FAILURE: Unit and Integration Tests",
                        body: "Unit and Integration Tests failed. See attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
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
                    emailext (
                        subject: "SUCCESS: Security Scan Completed",
                        body: "Security Scan completed successfully. See attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        subject: "FAILURE: Security Scan",
                        body: "Security Scan failed. See attached logs for details.",
                        to: "${EMAIL_RECIPIENT}",
                        attachLog: true
                    )
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
