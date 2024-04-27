pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-TEST', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://CDB4A0D5EA25E8E8A5CE2B1CE5B29195.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 20
                } 
            }
        }
        
        stage('verify deployemt') {
             steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-TEST', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://CDB4A0D5EA25E8E8A5CE2B1CE5B29195.gr7.us-east-1.eks.amazonaws.com']]) {
                     sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
