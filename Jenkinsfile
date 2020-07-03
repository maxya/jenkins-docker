pipeline {
    environment {
        registry = 'mysuperimage'
    }
    agent any
    stages {
        stage('node version in docker image') {
            agent {
                docker { image 'node:7-alpine' }
            }
            steps {
                sh 'node --version'
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('dockerstuff') {
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'newapp']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/maxya/jenkins-docker']]])
                    script {
                        docker.build registry + ":$BUILD_NUMBER"
                    }
                }
            }
        }
    }
}
