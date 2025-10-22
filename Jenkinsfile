pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    dir('src') {

                    withDockerRegistry(credentialsId: 'docker-rbid', toolName: 'docker') {
                        sh "docker build -t basha10/cartservice:latest ."
                    }
                        }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-rbid', toolName: 'docker') {
                        sh "docker push basha10/cartservice:latest "
                    }
                }
            }
        }
    }
}
