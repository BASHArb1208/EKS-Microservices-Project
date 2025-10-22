pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'RBEKS', contextName: '', credentialsId: 'RB-Token', namespace: 'rbapps', serverUrl: 'https://D9E7060F03C5394A3BCA2FD8A1C3055A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'RBEKS', contextName: '', credentialsId: 'RB-Token', namespace: 'RBapps', serverUrl: 'https://D9E7060F03C5394A3BCA2FD8A1C3055A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
