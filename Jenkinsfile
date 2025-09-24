pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials') // matches the new ID
        DOCKER_IMAGE = "msaisharan/jenkinsdemo"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MSaiSharan/Jenkins-Demo.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE:latest .'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests... (none yet)'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                    sh "docker push ${DOCKER_IMAGE}:latest"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh "docker run -d -p 3000:3000 $DOCKER_IMAGE:latest"
                }
            }
        }
    }
}
