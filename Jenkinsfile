// Updated Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Verify') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t sophia514/ecommerce-product-page .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credential', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    bat 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                    bat 'docker push sophia514/ecommerce-product-page'
                }
            }
        }
    }
}
