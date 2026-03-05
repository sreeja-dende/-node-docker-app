pipeline {
    agent any

    stages {

        stage('Clean Workspace') {
            steps {
                sh 'rm -rf node_modules'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                npm cache clean --force
                npm ci
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-docker-app:${BUILD_NUMBER} .'
            }
        }

        stage('Create Container') {
            steps {
                sh 'docker rm -f node-container || true'
                sh 'docker run -d -p 3000:8080 --name node-container node-docker-app:${BUILD_NUMBER}'
            }
        }

    }
}
