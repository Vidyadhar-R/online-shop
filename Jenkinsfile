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
                withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) {
                    sh "docker login -u vidyadhar7 -p ${DHPWD}"
                }
                sh 'sudo docker push vidyadhar7/e-commerce:latest'
            }
        }
    }
}
