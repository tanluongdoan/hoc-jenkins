pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/tanluongdoan/hoc-jenkins.git'
            }
        }
        stage('Build and Push Docker Image') {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                    sh 'docker build -t tanluongdoan/hoc-jenkins .'
                    sh 'docker push tanluongdoan/hoc-jenkins'
                }
            }
        }
    }
}
