pipeline {
    agent any
    triggers{ pollSCM ('') } 
    stages {
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
              mail body: "<b>ansible sample</b>
			 <br>Project: ${env.JOB_NAME} 
			 <br>Build Number: ${env.BUILD_NUMBER}
			 <br> URL de build: ${env.BUILD_URL}", 
			 charset: 'UTF-8', mimeType: 'text/html',
			 subject: "SUCCESS CI: Project name -> ${env.JOB_NAME}",
			 to: "nagajyothiperam@gmail.com";    
         }  
         failure { 
				
             mail body: "<b>ansible sample</b>
			 <br>Project: ${env.JOB_NAME} 
			 <br>Build Number: ${env.BUILD_NUMBER}
			 <br> URL de build: ${env.BUILD_URL}", 
			 charset: 'UTF-8', mimeType: 'text/html',
			 subject: "ERROR CI: Project name -> ${env.JOB_NAME}",
			 to: "nagajyothiperam@gmail.com";  
         }  
    }  
}
