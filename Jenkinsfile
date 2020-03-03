pipeline {
  agent any
  
   triggers {
       // poll repo at mentioned time in UTC
       pollSCM('30 14 * * *')
   }
	
  stages {
    stage('Clone git repo'){
     steps {
	//git 'https://github.com/officedepot/MCASA_Test.git'
	//sh 'ls -larth'
	//git credentialsId: 'f1333841-af04-4c11-8988-c4c26679fc34', url: 'https://github.com/shubhamorgtest/MCASA_TEST.git'
	sh 'pwd'
	sh 'ls'
	sh 'date'
	}
    }
	stage('Deploy via Tomcat'){
	 steps {
		 sh 'echo "Deploy in progress"'
		 //sh 'hostname -i'
		 //sh 'traceroute 10.94.0.75'
	//sshagent(['Mcasa_Test']) {
       //sh 'scp -o StrictHostKeyChecking=no /home/jenkins/agent/workspace/MCASA_TESTING/*.war ec2-user@10.94.0.75:/root/apache-tomcat-9.0.31/webapps/'
    //}
   }
  }
 }
}
