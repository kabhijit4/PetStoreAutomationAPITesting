pipeline {
    agent any

    triggers {
        cron('0 16 * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building..."
            }
        }

        stage('Test') {
            steps {
                echo "Running API Tests..."
            }
        }

        stage('Report') {
            steps {
                echo "Publishing Reports..."
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
