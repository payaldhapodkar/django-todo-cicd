pipeline {
    agent any

    stages {
        stage('Stop Container') {
            steps {
                script {
                    // Stop the container if it exists
                    def containerName = 'my-container'
                    sh "docker stop ${containerName} || true"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t todo-dev .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container
                    sh 'docker run -d -p 8081:8081 --name my-container todo-dev'
                }
            }
        }
    }

    post {
        always {
            // Clean up the Docker container after the build
            sh 'docker stop my-container || true'
            sh 'docker rm my-container || true'
        }
    }
}
