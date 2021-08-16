pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
                echo "BRANCH_NAME = ${env.BRANCH_NAME}"
                sh 'dotnet publish -c release --runtime linux-x64 HelloWorldVscode.csproj'

            
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
