pipeline {  
    agent any 
     tools {
	 maven 'apache-maven-3.8.4'	
	}
    stages { 
        stage('Build') { 
            steps { 
               echo 'This is a minimal pipeline.'
            }
        }
	stage('Maven Install'){
	    steps{
		sh "mvn clean install"
		}
	}		
    }
}

