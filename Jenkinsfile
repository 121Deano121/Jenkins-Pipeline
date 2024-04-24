pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo "Building ..."
            }
        }
    }
    post {
        success {
            mail to: "ilikebeans53@gmail.com",
            subject: "Build Status Email",
            body: "Build was Successful!"
        }
    }
}
