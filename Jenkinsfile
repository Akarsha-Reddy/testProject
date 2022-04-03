pipeline {  
    agent any 
     tools {
	 maven 'Maven_home'
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
              withSonarQubeEnv('SonarQube') {
                 sh 'mvn clean package sonar:sonar'
              }
          }
      }
	 stage("Jfrog server") {
		steps{
			rtServer (
                    id: "jfrog-server", 
                    url: "https://akarshreddy.jfrog.io",
                    username: 'jenkins',
			password: 'Ak@rsh56'
			bypassProxy: true,
			timeout: 300
                		)
		    }
	    }
	  stage("Jfrog upload") {
		steps{
		     rtUpload (
    			serverId: 'jfrog-server',
    			spec: '''{
         		 "files": [
           		 {
             			 "pattern": "*.war",
              			"target": "default-maven-local/"
           		 	}
        		 	]
   			 }''',
		      )
		    }
	    }
	    stage("Publish Build Info") {
		    steps{
		    rtPublishBuildInfo(
		    	serverId: 'jfrog-server'
		    )}
	    }
    }
}

