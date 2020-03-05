#!/usr/bin/env groovy

def schedule = env.BRANCH_NAME.contains('master') ? 'H/4 * * * *' : env.BRANCH_NAME == 'qa' ? 'H/3 * * * *' : ''


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
