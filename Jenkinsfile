pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Backend Syntax') {
            steps {
                dir('backend') {
                    bat 'npm install'
                    bat 'npm run check'
                }
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                dir('FRONTEND') {
                    bat 'npm install'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('FRONTEND') {
                    bat 'npm run build'
                }
            }
        }

        stage('TypeScript Check') {
            steps {
                dir('FRONTEND') {
                    bat 'npm run typecheck'
                }
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully!'
        }

        failure {
            echo 'CI pipeline failed. Check the Console Output.'
        }
    }
}