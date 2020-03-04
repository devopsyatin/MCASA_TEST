pipeline {
    agent {
        node {
            label 'snowflake'
        }
        }
options([enforceBuildSchedule(branches: ['master', 'qa'])])
    stages {
        stage ('Build'){
            steps {
                container ('sqitch'){
                    sh 'echo "Building"' 
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
