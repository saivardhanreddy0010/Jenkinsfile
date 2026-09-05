pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code downloaded from GitHub'
            }
        }

        stage('Build') {
            steps {
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                bat 'if exist index.html (echo Test PASSED) else (exit /b 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Application ready for deployment'
            }
        }
    }
}