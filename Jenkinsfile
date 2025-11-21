pipeline {
    agent any

    triggers {
        cron('0 17 * * *')
    }

    stages {

        stage('Build') {
            steps {
                echo "Building..."
                sh 'mvn clean test'
            }
        }

        stage('Test') {
            steps {
                echo "Running API Tests..."
            }
        }

        stage('Report') {
            steps {
                echo "Preparing Reports..."
            }
        }
    }

    post {
        always {
            echo "Publishing Results..."
            junit '**/surefire-reports/*.xml'
        }
    }
}
