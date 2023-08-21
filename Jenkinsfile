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
        // stage('Check if Container is Running') {
        //     steps {
        //         script {
        //             try {
        //                 // Check if the container is running
        //                 docker.image('todo-dev').inside('-p 8081:8081 --name my-container') {
        //                     // Do nothing, just check the container status
        //                 }
        //             } catch (Exception e) {
        //                 // If the container is not running, it will throw an exception
        //                 // Handle the exception here, or do nothing if you want to proceed anyway
        //             }
        //         }
        //     }
        // }
 
        // stage('Stop Existing Container') {
        //     steps {
        //         script {
        //             // Stop the container if it's already running
        //             try {
        //                 sh 'docker stop my-container'
        //             } catch (Exception e) {
        //                 // If the container is not running, it will throw an exception
        //                 // Handle the exception here, or do nothing if you want to proceed anyway
        //             }
        //         }
        //     }
        // }
        // stage('Conditional Stage') {
        //     when {
        //         expression {
        //             // Check if the PR contains a specific commit message
        //             return checkout(scm).pollingBaseline == null &&
        //                    checkout(scm).commits.any { commit -> commit.message.contains('specific-commit-message') }
        //         }
        //     }
        //     steps {
        //         script {
        //             // Steps to run when the condition is met
        //             echo "Running conditional steps"
        //         }
        //     }
        // }
//         stage('Conditional Stage') {
//             steps {
//                 script {
//                     def commitMessages = checkout(scm).commits.collect { it.message }
//                     echo "Commit messages: ${commitMessages.join('\n')}"
                    
//                     def shouldRun = checkout(scm).pollingBaseline == null &&
//                                    checkout(scm).commits.any { commit -> commit.message.contains('changes in file') }
//                     echo "Should run: ${shouldRun}"
//                 }
//             }
// }
        stage('Conditional Stage') {
            steps {
                script {
                    def savedCommitMessage = "Your expected commit message"
                    def commits = checkout(scm).commits
        
                    if (commits && commits.size() > 0) {
                        def currentCommitMessage = commits[0].message
        
                        echo "Saved Commit Message: ${savedCommitMessage}"
                        echo "Current Commit Message: ${currentCommitMessage}"
        
                        if (savedCommitMessage == currentCommitMessage) {
                            echo "Running conditional steps"
                            // Add your steps to run when the condition is met
                        } else {
                            echo "Skipping conditional steps"
                        }
                    } else {
                        echo "No commits found"
                    }
                }
            }
}


    
    //     stage('Run Docker Container') {
    //         steps {
    //             script {
    //                 // Remove the container if it's already running
    //                 docker.image('todo-dev').withRun('-p 8081:8081 --name my-container') {
    //                     // The above line will run the container and map port 8081 inside the container to port 8081 on the host machine
    //                     // Add any other configuration or environment variables if required for your application
    //                 }
    //             } 
    //         }
    //     }         
    // }
}
}

