pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('Docker Credentails') // match your Jenkins ID exactly
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
                    sh "echo $DOCKERHUB_CREDEN_
