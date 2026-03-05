pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sreeja-dende/-node-docker-app.git'
            }
        }

        stage('Clean Workspace') {
            steps {
                sh 'rm -rf node_modules'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-docker-app:${BUILD_NUMBER} .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f node-container || true'
            }
        }

        stage('Create Container') {
            steps {
                sh 'docker run -d -p 3000:8080 --name node-container node-docker-app:${BUILD_NUMBER}'
            }
        }

    }
}
