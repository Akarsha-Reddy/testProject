pipeline {  
    agent any 
     tools {
	 maven 'MAVEN_HOME' 	
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

