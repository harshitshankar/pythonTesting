pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/harshitshankar/pythonTesting.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the repo
                git url: "${REPO_URL}", branch: 'master'
            }
        }

        stage('Run Tests') {
            steps {
                // Move into the subfolder and run pytest using Windows batch commands
                dir('pythonsel') {
                    bat 'python -m pytest . --alluredir=..\\reports\\allure-results'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
        success {
            echo 'Tests passed!'
        }
        failure {
            echo 'Tests failed!'
        }
    }
}
