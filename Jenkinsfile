pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
                echo 'BRANCH_NAME = ${env.BRANCH_NAME}'
                dotnet publish -c release -v d -o "linux" --runtime linux-x64 HelloWorldVscode.csproj
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
