pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'project', serverUrl: 'https://19335B77E13EE43291A06FC39280AF5B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'project', serverUrl: 'https://19335B77E13EE43291A06FC39280AF5B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n project"
                }
            }
        }
    }
}
