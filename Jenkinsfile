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
        stage('Get Data from JSON') {
            // assign json data to env
            steps {
                /*script{
                    //env.json_data = "${sh(script:'cat nginx-var.json', returnStdout: true).trim()}"
                    env.json_data = sh(
                        script: ''' cat nginx-var.json''', returnStdout: true).trim()
		    echo "JSON_DATA = ${env.json_data}"
		}*/
		script{
                    //env.json_data = "${sh(script:'cat nginx-var.json', returnStdout: true).trim()}"
                    env.port = sh(
                        script: ''' cat nginx-var.json | jq .port  ''', returnStdout: true).trim()
		    echo "PORT = ${env.port}"
		}
		script{
                    //env.json_data = "${sh(script:'cat nginx-var.json', returnStdout: true).trim()}"
                    env.message = sh(
                        script: ''' cat nginx-var.json | jq .message  ''', returnStdout: true).trim()
		    echo "PORT = ${env.message}"
		}
            }
        
        }
    }
    
}
