pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "todo-dev:latest"
        // Replace "my-local-image" with the name you want for your local Docker image
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build("${DOCKER_IMAGE}", ".")
                }
            }
        }

        stage('Tag Docker Image') {
            steps {
                script {
                    docker.image("${DOCKER_IMAGE}").withRegistry('') {
                        // Empty registry URL to tag locally
                        docker.image("${DOCKER_IMAGE}").push("latest")
                    }
                }
            }
        }
    }
}
