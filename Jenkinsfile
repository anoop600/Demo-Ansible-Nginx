pipeline {
    agent any
    
    environment {
        port = 8080
        message = "hi from anoop"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/anoop600/Demo-Ansible-Nginx.git'
            }
        }
        stage('Print Environment Variables') {
            steps {
                // Get some code from a GitHub repository
                sh 'cat nginx-var.json'
            }
        }
        
    }
    
}
