pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR_USERNAME/docker-devops-project.git'
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
                bat 'docker rm -f devops-container || exit 0'
                bat 'docker run -d --name devops-container -p 8081:80 devops-docker-site'
            }
        }

        stage('Build Report') {
            steps {
                bat 'echo Build and Docker deployment successful > build-report.txt'
            }
        }
    }
}
