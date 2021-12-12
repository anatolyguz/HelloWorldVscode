#!groovy

properties([disableConcurrentBuilds()])


pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
        timestamps()
        skipDefaultCheckout(true)
    }
    
    stages {
        stage('Build') {
            steps {
             // Clean before build
                cleanWs()
                 // We need to explicitly checkout from SCM here
                checkout scm
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
          
          //echo IS_RELEASE
          
        
        
        
          steps {
              
              
   //          slackSend( color: "good", 
   //                     message: " -Message1 from Jenkins Pipeline \n -Message2 from Jenkins Pipeline" ,
   //                        channel: "test")

         
              
              
                echo "IS_RELEASE = ${env.IS_RELEASE}"
                script {
                    
                    
                    def attachments = [
  [
    text: """-I find your lack 
    -of faith disturbing! 
    """,
   "type": "mrkdwn",
    color: "good"
  ]
]
slackSend(channel: "#test",  message: "I am a test message", attachments: attachments)
                  
			
        def attachments = """[ { \"text\": \"And here’s an attachment!\" } ]"""
        echo (attachments)
        slackSend (channel: "#test", color: "danger", message: "Test message", attachments: attachments)
			
			
                    
                    
                    
blocks = [
	[
		"type": "section",
		"text": [
			"type": "mrkdwn",
			"text": "Hello, Assistant to the Regional Manager Dwight! *Michael Scott* wants to know where you'd like to take the Paper Company investors to dinner tonight.\n\n *Please select a restaurant:*"
		]
	],
    [
		"type": "divider"
	],
	[
		"type": "section",
		"text": [
			"type": "mrkdwn",
			"text": "*Farmhouse Thai Cuisine*\n:star::star::star::star: 1528 reviews\n They do have some vegan options, like the roti and curry, plus they have a ton of salad stuff and noodles can be ordered without meat!! They have something for everyone here"
		],
		"accessory": [
			"type": "image",
			"image_url": "https://s3-media3.fl.yelpcdn.com/bphoto/c7ed05m9lC2EmA3Aruue7A/o.jpg",
			"alt_text": "alt text for image"
		]
	]
]

slackSend(channel: "#test", blocks: blocks)                    
                    
                    
                    
                    
                    
                    if (env.IS_RELEASE == "True"){
                               
                        slackSend( color: "good", 
                        message: "Message from Jenkins Pipeline" ,
                           channel: "test")
                    }
                } 
           }
        }
          
        
        
    }
}
