pipeline {
    environment {
        registry = "mysuperimage"
    }
    agent any
    stages {
        stage('Test') {
    agent {
        docker { image 'node:7-alpine' }
    }
            steps {
                sh 'node --version'
            }
        }
        stage('Another Image') {
            steps{
                script {
                    docker.build registry + ":$BUILD_NUMBER"

                }

            }
        }
    }
}
