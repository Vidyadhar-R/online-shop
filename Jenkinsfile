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

        stage('PUSH image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubPassword', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                    sh "docker push vidyadhar7/e-commerce:latest"
                }
            }
        }
    }
}
