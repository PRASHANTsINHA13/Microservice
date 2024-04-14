pipeline { 
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-cred', namespace: 'webapps ', serverUrl: 'https://70A9C082F9F7152CC7B740A848A9BC18.yl4.ap-southeast-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-cred', namespace: 'webapps ', serverUrl: 'https://70A9C082F9F7152CC7B740A848A9BC18.yl4.ap-southeast-2.eks.amazonaws.com']]) {
                
                    sh"Kubectl get svc -n webapps"
                }
            }
        }
    }
}

