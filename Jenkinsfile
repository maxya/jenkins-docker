pipeline {
    environment {
        registry = "mysuperimage"
    }
    agent {
        docker { image 'node:7-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
        stage('Another Image') {
            steps{
                script {
                    docker.build registry + ":$BUILD_NUMBER"

                }
        step( [
                $class: 'DockerBuilderPublisher',
                cleanImages: false,
                cleanupWithJenkinsJobDelete: false,
                cloud: '', dockerFileDirectory: 'dockerstuff',
                fromRegistry: [],
                pushCredentialsId: '',
                pushOnSuccess: false,
                tagsString: 'mydocker'
                ])

            }
        }
    }
}
