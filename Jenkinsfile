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
            withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) {
                sh "docker login -u Vidyadhar7 -p ${DHPWD}"
                sh 'docker push Vidyadhar7/e-commerce:latest'
            }
        }
    }
}
