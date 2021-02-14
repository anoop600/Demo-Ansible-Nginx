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
        stage('Get Data') {
            // assign json data to env
            steps {
                script{
                    //env.json_data = "${sh(script:'cat nginx-var.json', returnStdout: true).trim()}"
                    env.json_data = sh(
                        script: ''' cat nginx-var.json''', returnStdout: true).trim()
		    echo "JSON_DATA = ${env.json_data}"
		}
		script{
                    //env.json_data = "${sh(script:'cat nginx-var.json', returnStdout: true).trim()}"
                    env.port = sh(
                        script: ''' jq .port ${env.json_data} ''', returnStdout: true).trim()
		    echo "PORT = ${env.port}"
		}
                /*script{
                    env.port = "${sh(script:"jq .port ${env.json_data}", returnStdout: true).trim()}"
                }
                script{
                    echo "JSON = ${env.json_data}"
                }
                script{
                    echo "PORT = ${env.port}"
                }*/
            }
        
        }
    }
    
}
