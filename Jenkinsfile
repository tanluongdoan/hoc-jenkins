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
                    bat 'docker build -t tanluongdoan/hoc-jenkins .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    def username = credentialsId('tanluong.doan@gmail.com', environment: true).username
                    def password = credentialsId('DTL1a25uo29!', environment: true).password
                    docker login - u "$username" - p "$password"
                     bat 'docker push tanluongdoan/hoc-jenkins' // Replace with your image name
                }
            }
        }
    }
}
