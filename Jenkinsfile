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
        stage("Override Variables") {
            // assign json data to env
	    environment {
		port = 8080
		message = "hi from anoop"
	    }
            steps {
		script{
                    env.port = sh(
                        script: ''' cat nginx-var.json | jq .port  ''',
			returnStdout: true
		    ).trim()
		    echo "PORT = ${env.port}"
		}
		script{
                    env.message = sh(
                        script: ''' cat nginx-var.json | jq .message  ''',
			returnStdout: true
		    ).trim()
		    echo "Message = ${env.message}"
		}
            }
        
        }
    }
    
}
