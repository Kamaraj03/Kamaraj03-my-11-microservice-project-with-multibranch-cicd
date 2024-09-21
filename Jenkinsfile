pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '11-microservices-project-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'ecommerce', serverUrl: 'https://FAE13E3C23057A05CEDE829F670693C9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '11-microservices-project-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'ecommerce', serverUrl: 'https://FAE13E3C23057A05CEDE829F670693C9.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n ecommerce"
                }
            }
        }
    }
}
