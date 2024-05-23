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
                    sh 'docker build -t tanluongdoan/hoc-jenkins .'
                }
            }
        }
        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             // Đăng nhập vào Docker Hub
        //             sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                    
        //             // Đẩy Docker image lên Docker Hub
        //             sh 'docker push tanluongdoan/hoc-jenkins'
        //         }
        //     }
        // }
    }
}
