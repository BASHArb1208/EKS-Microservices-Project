pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-rbid', toolName: 'docker') {
                        sh "docker build -t basha10/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-rbid', toolName: 'docker') {
                        sh "docker push basha10/adservice:latest "
                    }
                }
            }
        }
    }
}
