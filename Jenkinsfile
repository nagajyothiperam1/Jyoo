pipeline {
    agent any
    stages {
		stage('mail'){
			steps{
				emailext body: 'test!!!!!!!!!!', subject: 'Job Started', to: 'nagajyothiperam@gmail.com'
            }
		}
		stage('load'){
			steps{
				script{
					sh "ansible-playbook apache.yml"
				}
			}
		}
        
    }
	post {   
        success {  
            emailext ( subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
			console output: <a href="${env.BUILD_URL}/console">${env.JOB_NAME} _${env.BUILD_NUMBER}</a>""",
			to: "nagajyothiperam@gmail.com",   
        }  
        failure { 
	        emailext ( subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
			console output: <a href="${env.BUILD_URL}/console">${env.JOB_NAME} _${env.BUILD_NUMBER}</a>""",
			to: "nagajyothiperam@gmail.com", 
        }  
    }  
}
