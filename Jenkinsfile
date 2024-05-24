pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub') // Sử dụng ID của credentials mà bạn đã cấu hình
    }
    stages {
        stage('Clone') {
            steps {
                // Clone repository từ GitHub
                git branch: 'main', url: 'https://github.com/tanluongdoan/hoc-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                 script {
                    // Build Docker image
                    bat 'docker build -t tanluongdoan/hoc-jenkins .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
               script {
                    // Đăng nhập vào Docker Hub
                    withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
                        bat 'echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin' // Sử dụng 'sh' cho môi trường Unix/Linux
                        // bat 'echo %DOCKERHUB_PASSWORD% | docker login -u %DOCKERHUB_USERNAME% --password-stdin' // Sử dụng 'bat' cho môi trường Windows
                        
                        // Đẩy Docker image lên Docker Hub
                        bat 'docker push tanluongdoan/hoc-jenkins' // Sử dụng 'sh' cho môi trường Unix/Linux
                        // bat 'docker push tanluongdoan/hoc-jenkins' // Sử dụng 'bat' cho môi trường Windows
                    }
                }
            }
        }
    }
}
