pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'jenkins', serverUrl: 'https://7B2CC503D3571845476EFFD813E9B51D.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'jenkins', serverUrl: 'https://7B2CC503D3571845476EFFD813E9B51D.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n jenkins"
                }
            }
        }
    }
}
