pipeline {
  agent any
  
triggers { 
	pollSCM('10 12 * * *') 
	}
	
  stages {
    stage('Clone git repo'){
     steps {
	sh 'pwd'
	     
	sh 'ls'
	sh 'date'
	}
    }
   stage('Deploy via Tomcat'){
    steps {
	 sh 'echo "Deploy in progress"'
	  }
  	}
    }
}
