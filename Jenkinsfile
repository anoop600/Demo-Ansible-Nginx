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
        stage("Execute Ansible Script") {
		// assign json data to env
		environment {
			def config = readJSON file: 'nginx-var.json'
			port = "${config.port}"
			message = "${config.message}"
		}
		steps {
			script{
				env.port = sh(
					script: " cat nginx-var.json | jq .port ",
					returnStdout: true
				).trim()
				echo "PORT = ${env.port}"
			}
		}
        }
    }
}
