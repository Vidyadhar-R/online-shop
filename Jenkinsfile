pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            steps {
                git url: 'https://github.com/Vidyadhar-R/online-shop.git'
            }
        }

        stage('Run Docker Compose File') {
            steps {
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
        }

        stage('Build and Push Docker Image') {
            environment {
                DOCKER_IMAGE = "vidyadhar7/e-commerceapp_web:${BUILD_NUMBER}"
                // DOCKERFILE_LOCATION = "php/online-shopping-system/Dockerfile"
                REGISTRY_CREDENTIALS = credentials('dockerhub')
            }
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "dockerhub") {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
