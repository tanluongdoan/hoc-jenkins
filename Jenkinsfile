pipeline {
    agent any
    environment {
        DOCKER_USERNAME = 'tanluong.doan@gmail.com'
        DOCKER_PASSWORD = credentials('DTL1a25uo29!') // Thay 'docker-hub-password' bằng ID của credentials bạn đã cấu hình
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/tanluongdoan/hoc-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t tanluongdoan/hoc-jenkins .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    echo "${env.DOCKER_PASSWORD}" | docker login -u "${env.DOCKER_USERNAME}" --password-stdin
                    bat 'docker push tanluongdoan/hoc-jenkins'
                }
            }
        }
    }
}
