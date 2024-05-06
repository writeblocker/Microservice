pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://FE93C17A2383B040747551F045E58BBD.yl4.us-east-1.eks.amazonaws.com']]) {
               sh "kubectl apply -f deployment-service.yml"
               sleep 60
               }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://FE93C17A2383B040747551F045E58BBD.yl4.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
