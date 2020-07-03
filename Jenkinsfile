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
            dir('dockerstuff') {

            steps{
                git https://github.com/maxya/jenkins-docker
                script {
                    docker.build registry + ":$BUILD_NUMBER"

                }

            }
            }
        }
    }
}
