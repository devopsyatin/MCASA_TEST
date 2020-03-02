pipeline {
  agent any
  
  stages {
    stage('Clone git repo'){
     steps {
	//git 'https://github.com/officedepot/MCASA_Test.git'
	sh 'ls -larth'
	git credentialsId: 'f1333841-af04-4c11-8988-c4c26679fc34', url: 'https://github.com/shubhamorgtest/MCASA_TEST.git'
	sh 'pwd'
	sh 'ls'
	}
    }
  }
}
