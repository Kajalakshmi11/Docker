pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "first_app"
        CONTAINER_NAME = "determined_johnson"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Kajalakshmi11/Docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %DOCKER_IMAGE% ."
            }
        }

        stage('Stop and Remove Previous Container') {
            steps {
                bat 'FOR /F "tokens=*" %i IN (\'docker ps -a -q -f "name=determined_johnson"\') DO docker rm -f %i'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat "docker run -d -p 3000:3000 --name %CONTAINER_NAME% %DOCKER_IMAGE%"
            }
        }

        stage('Check Running Containers') {
            steps {
                bat 'docker ps'
            }
        }
    }

    post {
        failure {
            echo 'There was an error with the build process.'
        }
    }
}
