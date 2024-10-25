pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://646BAAFC2223C28676BBD0EBFA2C0C2F.gr7.ap-south-1.eks.amazonaws.com']]) {
            sh "kubectl apply -f deployment-service.yml"
            sleep 60
               }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://646BAAFC2223C28676BBD0EBFA2C0C2F.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
