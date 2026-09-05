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
                bat 'docker build -t my-jenkins-app .'
            }
        }

        stage('Test') {
            steps {
                bat 'if exist index.html (echo Test PASSED) else (exit /b 1)'
            }
        }

        stage('Credentials Test') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'my-test-credentials',
                        usernameVariable: 'MY_USER',
                        passwordVariable: 'MY_PASSWORD'
                    )
                ]) {
                    bat 'echo Username is %MY_USER%'
                    bat 'echo Password is %MY_PASSWORD%'
                }
            }
        }

        stage('Environment Info') {
            steps {
                bat 'echo Build Number: %BUILD_NUMBER%'
                bat 'echo Job Name: %JOB_NAME%'
                bat 'echo Workspace: %WORKSPACE%'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Application ready for deployment'
            }
        }
    }

    post {

        success {
            echo 'SUCCESS: Pipeline completed'
        }

        failure {
            echo 'FAILURE: Pipeline failed'
        }

        always {
            echo 'Pipeline has finished'
        }
    }
}