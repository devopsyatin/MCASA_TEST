#!groovy

//def call(body) {
//  def config = [:]
//  body.resolveStrategy = Closure.DELEGATE_FIRST
//  body.delegate = config
//  body()

//import hudson.model.*
//import hudson.EnvVars
//import groovy.json.JsonSlurperClassic
//import groovy.json.JsonBuilder
//import groovy.json.JsonOutput
//import java.net.URL


def schedule = env.BRANCH_NAME.contains('master') ? 'H/4 * * * *' : env.BRANCH_NAME == 'qa' ? 'H/3 * * * *' : ''

	
pipeline {
	triggers {
         	pollSCM(schedule) 
		}
agent any
    stages {
        stage ('Setup Env Vars'){
        steps {
          script {
                def gitCommit = sh(returnStdout: true, script: 'git rev-parse HEAD')
                echo "gitCommit= ${gitCommit}"
                    }
                }
            }
        stage ('Build'){
            steps {
                //container ('sqitch'){
                    sh 'echo "Building"' 
                    sh 'echo "testing"'
                    sh 'echo "testing cron"'
                //}
            }
        }
        stage ('Push WAR to Nexus'){
            steps {
                //container ('sqitch'){
                    script {
                        echo "Uploading to Nexus"
                    }
                //}
            }
        }
        stage ('Execute Tower Playbook'){
            steps {
                //container ('sqitch'){
		  //steps {
                    script {
                        echo "Branch == ${env.BRANCH_NAME}"
                        if ( "${env.BRANCH_NAME}" == "master" )
                            {
                             //checkout scm
                             //env.changefile = readTrusted('ChangeRequest.txt')
                             //lines = env.changefile.readLines()
                             //env.ChangeNumber = lines.get(0)
                             //echo "ServiceNow number used for this deployment is: ${env.ChangeNumber}"
	                     //    outsideChange("oddev","${env.ChangeNumber}",999,"NONE","[code]<p> Jenkins Build: ${env.BUILD_TAG}</p><br><br><p>" + "</p>[code]")   
                            echo "This would deploy to PROD"
                            } 
                        else if ( "${env.BRANCH_NAME}" == "qa" )
                            {
                            echo "This would deploy to UAT"
                            } 
                        else if ( "${env.BRANCH_NAME}" == "Development" )
                            {
                            echo "This would deploy to Development"
        	                    }
                	        }
                    	    }
                	}
            	    }
post {
      success {
         script{
           if ( "${env.BRANCH_NAME}" == "master" )
                  { 
                echo 'PROD Deployment Successful !!!'
		jiraSendDeploymentInfo environmentId: '', environmentName: '', environmentType: 'production', site: 'jira-jenkins-test.atlassian.net'
		jiraSendBuildInfo branch: 'master', site: 'jira-jenkins-test.atlassian.net'
		  }
	   else if ( "${env.BRANCH_NAME}" == "qa" )
                  {
                  echo 'QA Deployment Successful !!!'
		  }
		 }
      		}
    	    }
	
	}
    //}
