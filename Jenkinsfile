pipeline {
    agent any

    environment {
        FRONTEND_DIR = 'frontend'  
        BACKEND_DIR = 'backend'    
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Kajalakshmi11/Docker.git'
            }
        }

        stage('Build Frontend') {
            steps {
                dir(FRONTEND_DIR) {
                    echo 'Installing frontend dependencies...'
                    sh 'npm install'
                    
                    echo 'Building React app...'
                    sh 'npm run build'
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir(BACKEND_DIR) {
                    echo 'Installing backend dependencies...'
                    sh 'npm install'
                }
            }
        }

        stage('Test (Optional)') {
            steps {
                echo 'Running tests... (Add test commands if you have any)'
                // Example: sh 'npm run test'
            }
        }

        stage('Deploy (Optional)') {
            steps {
                echo 'Deploy step here (like Docker build, AWS deploy, etc.)'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
