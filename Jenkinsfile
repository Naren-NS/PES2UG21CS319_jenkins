pipeline {
    agent {
        label 'docker'
    }

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Naren-NS/jenkins.git'
            }
        }

        stage('Install dependencies') {
            steps {
                script {
                    // Install Node.js and npm
                    sh 'apt-get update && apt-get install -y nodejs npm'
                    sh 'npm install'
                }
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
                script {
                    sh 'docker build -t naren-ns/my-image:$BUILD_NUMBER .'
                    sh 'docker push naren-ns/my-image:$BUILD_NUMBER'
                }
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
