pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C7E57F325F27BF6566ED5F45844E4F54.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
         stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C7E57F325F27BF6566ED5F45844E4F54.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
               }
            }
        }
        
    }
}
