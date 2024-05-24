pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/tanluongdoan/hoc-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t hoc-jenkins .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    
                    bat 'docker tag hoc-jenkins tanluongdoan/hoc-jenkins:0.0.0'
                    bat 'docker tanluongdoan/hoc-jenkins:0.0.0'
                }
            }
        }
    }
}
