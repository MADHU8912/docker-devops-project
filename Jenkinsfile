pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MADHU8912/docker-devops-project.git'
            }
        }

        stage('Check Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Check Docker') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-docker-site .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker rm -f devops-container >nul 2>&1 || exit /b 0'
                bat 'docker run -d --name devops-container -p 8082:80 devops-docker-site'
            }
        }

        stage('Build Report') {
            steps {
                bat 'echo Build and Docker deployment successful > build-report.txt'
            }
        }
    }
}
