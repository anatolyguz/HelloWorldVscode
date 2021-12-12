#!groovy

properties([disableConcurrentBuilds()])


pipeline {
    agent any
    triggers {
        githubPush()
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
             
            }
        }
  
      stage('Send to slack') {
  
          when { branch 'master' }
  
          environment {
                  IS_RELEASE = """${sh(
                   returnStdout: true,
                   script:   '''#!/bin/bash
                        #echo "WORKSPACE = $WORKSPACE"
                        cd $WORKSPACE
                        #git pull
                        COMMIT_WITH_LAST_TAG=$(git rev-list --tags --max-count=1)
                        #echo "COMMIT_WITH_LAST_TAG = $COMMIT_WITH_LAST_TAG"
                        LAST_COMMIT=$(git log --pretty=format:"%H" -1)
                        #echo "LAST_COMMIT = $LAST_COMMIT"
                        IS_RELEASE="False"
                        if [[ $LAST_COMMIT == $COMMIT_WITH_LAST_TAG ]]; then 
                            IS_RELEASE="True"
                        fi
                        #echo "IS_RELEASE = $IS_RELEASE"
                        echo "$IS_RELEASE"
                '''
                   )}"""
           
          }       
          
          echo IS_RELEASE
          
          when { 
               expression { IS_RELEASE == "True" }
               }
          
          
          steps {
         
              slackSend( color: "good", 
                        message: "Message from Jenkins Pipeline" ,
                           channel: "test")
            
            }
        }
          
        
        
    }
}
