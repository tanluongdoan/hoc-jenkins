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
                    withCredentials([usernamePassword(credentialsId: 'DTL1a25uo29!', usernameVariable: 'tanluong.doan@gmail.com', passwordVariable: 'DTL1a25uo29!')]) {
                        echo "${DOCKER_PASSWORD}" | docker login - u "${DOCKER_USERNAME}" - password - stdin
                        bat 'docker push tanluongdoan/hoc-jenkins'
                    }
                }
            }
        }
    }
}
