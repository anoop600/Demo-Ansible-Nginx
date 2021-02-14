pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/anoop600/Demo-Ansible-Nginx.git'
            }
        }
        
    }
    stage('Cat') {
            steps {
                // Get some code from a GitHub repository
                cat 'nginx-var.json'
            }
        }
}
