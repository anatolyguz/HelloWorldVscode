#!groovy

properties([disableConcurrentBuilds()])

pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
        timestamps()
        //skipDefaultCheckout(true)
    }
    
    stages {
        stage('Build') {
            steps {
                // Clean before build
                //cleanWs()
                 // We need to explicitly checkout from SCM here
                //checkout scm
                echo 'Building linux..'
                sh 'env'
                echo "banch = $banch"
                echo "tag = $tag"
                
    //     }

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
       
        stage('Deploy release') {
            when { tag 'release_*' }
 
            steps {
                echo 'Deploying release....'
            }
        }

       stage('Deploy beta') {
            when { tag 'beta_*' }
 
            steps {
                echo 'Deploying release....'
            }
        }



  
    //   stage('Send to slack') {
 
    //       when { branch 'master' }
    //         echo "banch = master"
    //     }

        //   environment {

        //            IS_RELEASE = """${sh(
        //            returnStdout: true,
        //            script:   '''#!/bin/bash
        //                 #echo "WORKSPACE = $WORKSPACE"
        //                 cd $WORKSPACE
        //                 #git pull
        //                 COMMIT_WITH_LAST_TAG=$(git rev-list --tags --max-count=1)
        //                 #echo "COMMIT_WITH_LAST_TAG = $COMMIT_WITH_LAST_TAG"
        //                 LAST_COMMIT=$(git log --pretty=format:"%H" -1)
        //                 #echo "LAST_COMMIT = $LAST_COMMIT"
        //                 IS_RELEASE="False"
        //                 if [[ $LAST_COMMIT == $COMMIT_WITH_LAST_TAG ]]; then 
        //                     IS_RELEASE="True"
        //                 fi
        //                 #echo "IS_RELEASE = $IS_RELEASE"
        //                 echo "$IS_RELEASE"
        //         '''
        //        )}"""
           
        //     }       
          
        //   //echo IS_RELEASE
          
      
          
        
        
    }
}
