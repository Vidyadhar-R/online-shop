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

        stage('Build Docker Image') {
            steps {
                script {
                    // Build your Docker image
                    sh 'docker build -t e-commerceapp_web .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Login to Docker Hub
                    withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) {
                        sh "docker login -u Vidyadhar7 -p ${DHPWD}"

                        // Push the Docker image to Docker Hub
                        sh 'docker push Vidyadhar7/e-commerce:latest'
                    }
                }
            }
        }
    }
}
