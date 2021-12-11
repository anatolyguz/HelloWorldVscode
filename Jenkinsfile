pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
                script {
                    def nextVersion = getNextSemanticVersion()
                    println "Next version:" + nextVersion.toString();
                    println " Major:" + nextVersion.getMajor();
                    println " Minor:" + nextVersion.getMinor();
                    println " Patch:" + nextVersion.getPatch();
                }
                
                
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
    }
}
