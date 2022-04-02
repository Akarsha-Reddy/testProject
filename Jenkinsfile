pipeline {  
    agent any 
     tools {
	 maven 'Maven_home' 
	 sonar 'SonarQube_scanner_home'
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
	stage("build & SonarQube analysis") {
          steps {
              withSonarQubeEnv('My SonarQube Server') {
                 sh 'mvn clean package sonar:sonar'
              }
          }
      }
    }
}

