pipeline {
    agent any
    
    stages {
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
        
        stage("My stage") {            
            steps {
                bat label: 'My batch script',
                    script: ''' @echo off
                                return_1_if_success.exe   // command which returns 1 in case of success, 0 otherwise
                                IF %ERRORLEVEL% EQU 1 (exit /B 0) ELSE (exit /B 1)'''
                }
            }
    }
}
