pipeline {
    agent any

    triggers {
        cron('0 17 * * *')   // Runs every day at 4 PM IST
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Running Maven Build on Windows..."
                bat "mvn clean install -DskipTests=false"
            }
        }

        stage('Run Tests') {
            steps {
                echo "Running TestNG Tests..."
                bat "mvn test"
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

            // Publish TestNG XML report
            junit 'test-output/testng-results.xml'

            // Optional: archive your entire test-output folder
            archiveArtifacts artifacts: 'test-output/**/*.*', allowEmptyArchive: true

            echo "Pipeline finished."
        }
    }
}
