pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR_USERNAME/docker-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-docker-site .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8080:80 devops-docker-site'
            }
        }

        stage('Build Report') {
            steps {
                bat 'echo Build Success > build-report.txt'
            }
        }
    }
}