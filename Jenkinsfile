pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
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