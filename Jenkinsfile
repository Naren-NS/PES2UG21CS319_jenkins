pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Naren-NS/jenkins.git' // Replace with your GitHub repository URL
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build application') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test application') {
            steps {
                sh 'npm test'
            }
        }

        stage('Push Docker image') {
            steps {
                sh 'docker build -t naren-ns/my-node-app:$BUILD_NUMBER .' // Replace with your Docker Hub username and image name
                sh 'docker push naren-ns/my-node-app:$BUILD_NUMBER'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Additional success steps can be added here.'
        }
        failure {
            echo 'Pipeline failed! Additional failure steps can be added here.'
        }
    }
}
