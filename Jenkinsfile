pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your version control system
                git 'https://github.com/your/repo.git'
            }
        }

        stage('Build') {
            steps {
                // Compile the .cpp file using a shell script
                sh 'g++ -o my_executable your_cpp_file.cpp'
            }
        }

        stage('Test') {
            steps {
                // Print output of the .cpp file using a shell script
                sh './my_executable'
            }
        }

        stage('Deploy') {
            steps {
                // Placeholder for deployment steps
                echo 'Deployment steps go here'
            }
        }
    }

    post {
        success {
            // Additional steps to execute when the pipeline is successful
            echo 'Pipeline executed successfully!'
        }

        failure {
            // Additional steps to execute when the pipeline fails
            echo 'Pipeline failed! Check the logs for details.'
        }
    }
}
