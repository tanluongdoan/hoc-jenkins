pipeline {
    agent any
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
                    bat 'docker login -u tanluong.doan@gmail.com -p DTL1a25uo29!'
                    bat 'docker push tanluongdoan/hoc-jenkins'
                }
            }
        }
    }
}
