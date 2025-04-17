pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo '📥 Checking out source code...'
                checkout scm
                git branch: 'main', url: 'https://github.com/DhanushNadar/Kubenaut.git'
            }
        }
        
        stage('Deploy to Kubernetes') {
            steps {
                echo '🚀 Deploying application to Kubernetes...'
                sh '''
                    kubectl apply -f manifests/deployment.yml
                    kubectl apply -f manifests/service.yml
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
