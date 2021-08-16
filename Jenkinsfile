pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
                echo "BRANCH_NAME = ${env.BRANCH_NAME}"
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
