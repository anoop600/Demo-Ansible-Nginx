pipeline {
    agent any
    
    environment {
	def config = readJSON file: 'nginx-var.json'
	port = 8080
	message = "Hi from anoop Its v1"
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
	stage('Ansible Ping all hosts') {
		steps{
			sh "ansible centos -m ping -i ${WORKSPACE}/inventory/hosts"
		}
	}
	stage('Ansible Execution') {
		environment {
			def config = readJSON file: 'nginx-var.json'
			port = "${config.port}"
			message = "${config.message}"
		}
		steps{
			sh "ansible-playbook -i ${WORKSPACE}/inventory/hosts ${WORKSPACE}/ansible-script/first-playbok.yml -e \"port=${env.port} message=${env.message}\""
		}
	}
    }
}
