pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'Demo', contextName: '', credentialsId: 'K8S_Token', namespace: 'webapps', serverUrl: 'https://CC55A7AF568BA3FD585B503352FB7214.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'Demo', contextName: '', credentialsId: 'K8S_Token', namespace: 'webapps', serverUrl: 'https://CC55A7AF568BA3FD585B503352FB7214.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
