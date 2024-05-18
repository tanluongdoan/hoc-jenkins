// pipeline {
//     agent any
//     stages {
//         stage('Clone') {
//             steps {
//                 git branch: 'main', url: 'https://github.com/tanluongdoan/hoc-jenkins.git'
//             }
//         }
//         stage('Build and Push Docker Image') {
//             steps {
//                 withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
//                     sh 'docker build -t tanluongdoan/hoc-jenkins .'
//                     sh 'docker push tanluongdoan/hoc-jenkins'
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub') // Use the credentials ID you've configured
    }
    stages {
        stage('Clone') {
            steps {
                // Clone the Git repository
                git branch: 'main', url: 'https://github.com/tanluongdoan/hoc-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t tanluongdoan/hoc-jenkins .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Login to Docker Hub
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                    
                    // Push the Docker image to Docker Hub
                    sh 'docker push tanluongdoan/hoc-jenkins'
                }
            }
        }
    }
}
