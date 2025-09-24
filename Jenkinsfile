pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
        DOCKER_IMAGE = "msaisharan/jenkinsdemo"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out GitHub repository...'
                git branch: 'main', url: 'https://github.com/MSaiSharan/Jenkins-Demo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t $DOCKER_IMAGE:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests... (none yet)'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                echo 'Logging in to Docker Hub and pushing image...'
                sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                sh "docker push ${DOCKER_IMAGE}:latest"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Docker container locally on port 3000...'
                sh "docker run -d -p 3000:3000 $DOCKER_IMAGE:latest"
            }
        }
    }
}
