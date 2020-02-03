pipeline {
    agent any
    triggers{ pollSCM ('* * * * *') } 
    stages {
	stage('load'){
	    steps{
		script{
		sh "ansible-playbook apache.yml"
		}
	    }
	}
        
    }
}