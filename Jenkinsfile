pipeline {
    agent any

    stages {
        // stage('Clone Repository') {
        //     steps {
        //         // Clone the GitHub repository
        //         git 'https://github.com/payaldhapodkar/django-todo-cicd.git'
        //     }
        // }

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
    post {
        always {
            // Clean up the Docker image and container after the build
            cleanWs()
            docker.image('todo-dev').clean(ws: true, message: '') // Provide an empty message parameter
            sh 'docker container rm my-container -f'
        }
    }

}
