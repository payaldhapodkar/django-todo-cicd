pipeline {
    agent any
        stage('Build Docker Image') {
            steps {
                script {
                    // Replace 'your-docker-image' with the name of your Docker image
                    dockerImage = docker.build('todo-dev')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Remove the container if it's already running
                    docker.image('todo-dev').withRun('-p 8081:8081 --name my-container') {
                        // The above line will run the container and map port 8081 inside the container to port 8081 on the host machine
                        // Add any other configuration or environment variables if required for your application
                    }
                }
            }
        }
    }

}
