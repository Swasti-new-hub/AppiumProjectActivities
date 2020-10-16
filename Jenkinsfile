pipeline{
    agent any
	environment{
	  JAVA_HOME='/usr/lib/jvm/java'
	  }
	  
	  stages{
	   stage ('Build'){
	    steps {
		     sh 'mvn compile'
			  }
			 }
			 stage ('Test'){
			    steps {
				   wrap ([$class: 'Xvfb', debug: true, displayName: 99, displayNameOffset: 0, timeout: 15]){
				   
				  sh 'mvn test'
           }
  }
  }
  stage('Publish'{
   steps{
     step ($class: 'Publisher' , reportFilenamePattern: **testng-results.xml, 
	 escapeExceptionmsg: true, escapeTestDescription: true, failureOnTestConfig: false, showFailedBuilds: false, thresholdMode: 2, unstableSkips: 100, failedSkips: 100, unstableFails: 0, failedFails: 100])
	  stage('Post') {
            steps {
                echo 'Tests finished'
            }
        }
    }
}

	 
	   