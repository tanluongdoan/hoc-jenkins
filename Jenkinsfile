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
                    // This step should not normally be used in your script. Consult the inline help for details.
                    withDockerRegistry(credentialsId: 'docker-hub', url: ' https://index.docker.io/v1/') {
                        bat 'docker tag hoc-jenkins tanluongdoan/hocjenkins:0.0.0'
                        bat 'docker push tanluongdoan/hocjenkins:0.0.0'
                    }

                }
            }
        }
    }
}
