pipeline {
  agent any
	options {
    enforceBuildSchedule()
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
