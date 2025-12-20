pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "chakri8991/imageecom"
        TAG = "v1"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/chakri8991/devopsecom1.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:$TAG .'
            }
        }

        stage('Push Image') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pass', variable: 'PASS')]) {
                    sh '''
                    docker login -u chakri8991 -p $PASS
                    docker push $DOCKER_IMAGE:$TAG
                    '''
                }
            }
        }
    }
}

