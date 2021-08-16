pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building linux..'
                echo "BRANCH_NAME = ${BRANCH_NAME}"
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
