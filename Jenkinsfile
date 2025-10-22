pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'RBBEKS', contextName: '', credentialsId: 'RB-Token', namespace: 'rbapps', serverUrl: 'https://68E35C2098A26E047CB0EED9AEFF23AB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'RBBEKS', contextName: '', credentialsId: 'RB-Token', namespace: 'rbapps', serverUrl: 'https://68E35C2098A26E047CB0EED9AEFF23AB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n rbapps"
                }
            }
        }
    }
}
