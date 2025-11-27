pipeline {
    agent any  // Runs on any available agent
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // You can add build commands here, e.g., invoking Maven, Gradle, etc.
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // You can add test commands here, e.g., running unit tests
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // You can add deployment commands here, e.g., using Docker or Kubernetes
            }
        }
    }
}
