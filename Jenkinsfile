pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
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
                bat 'docker ps'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t ats-site .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker rm -f ats-container || exit 0'
                bat 'docker run -d -p 8080:80 --name ats-container ats-site'
            }
        }

        stage('Build Report') {
            steps {
                echo 'Build and deployment completed successfully'
            }
        }
    }
}
stage('Run Container') {
    steps {
        bat 'docker rm -f ats-container || exit 0'
        bat 'docker run -d --name ats-container -p 8080:80 ats-site'
    }
}
