pipeline {
    agent any
    
    environment {
	def config = readJSON file: 'nginx-var.json'
	port = "${config.port}"
	message = "${config.message}"
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
	stage('Ansible Execution') {
		ansiblePlaybook(
			"credentialsId": 'azureuser',
			"disableHostKeyChecking": true,
			"inventory": '${WORKSPACE}/inventory/hosts',
			"colorized": true,
			"playbook": '${WORKSPACE}/ansible-script/first-playbok.yml'
		)
	}
    }
}
