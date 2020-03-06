#!/usr/bin/env groovy

//import hudson.model.*
//import hudson.EnvVars
//import groovy.json.JsonSlurperClassic
//import groovy.json.JsonBuilder
//import groovy.json.JsonOutput
//import java.net.URL


def schedule = env.BRANCH_NAME.contains('master') ? 'H/4 * * * *' : env.BRANCH_NAME == 'qa' ? 'H/3 * * * *' : ''
//def commit = sh(script: '{ git log -1 --pretty=format:\'%an\'; echo "@yahoo.in, developer@yahoo.in"; } | xargs -I{} echo {} | sed \'s/\n//\'', returnStdout: true).trim()

pipeline {
    agent {
        node {
            label 'snowflake'
        }
        }
    options {
    enforceBuildSchedule()
            }
    
   
     triggers {
      cron(schedule)
    }
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
                container ('sqitch'){
                    sh 'echo "Building"' 
                    sh 'echo "testing"'
                    sh 'echo "testing cron"'
                }
            }
        }
        stage ('Push WAR to Nexus'){
            steps {
                container ('sqitch'){
                    script {
                        echo "Uploading to Nexus"
                    }
                }
            }
        }
        stage ('Execute Tower Playbook'){
            steps {
                container ('sqitch'){
                    script {
                        echo "Branch == ${env.BRANCH_NAME}"
                        if ( "${env.BRANCH_NAME}" == "master" )
                            {
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
        }
    }
