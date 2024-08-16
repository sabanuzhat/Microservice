pipeline {
    agent any

    stages {
        stage('Deploy To K8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B7F948F9F5C496B095D08F2C6C120089.sk1.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B7F948F9F5C496B095D08F2C6C120089.sk1.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
