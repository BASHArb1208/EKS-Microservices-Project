pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(
                    kubectlCredentials: [[
                        credentialsId: 'rbtoken',
                        serverUrl: 'https://68E35C2098A26E047CB0EED9AEFF23AB.gr7.us-east-1.eks.amazonaws.com',
                        clusterName: 'RBBEKS',
                        namespace: 'rbapps'
                    ]]
                ) {
                    sh 'kubectl apply -f deployment-service.yml -n rbapps'
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeCredentials(
                    kubectlCredentials: [[
                        credentialsId: 'rbtoken',
                        serverUrl: 'https://68E35C2098A26E047CB0EED9AEFF23AB.gr7.us-east-1.eks.amazonaws.com',
                        clusterName: 'RBBEKS',
                        namespace: 'rbapps'
                    ]]
                ) {
                    sh 'kubectl get all -n rbapps'
                }
            }
        }
    }
}
