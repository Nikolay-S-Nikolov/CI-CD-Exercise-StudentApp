pipeline {
    agent any

    environment {
        NODE_ENV = 'development'
    }

    tools {
        nodejs 'NodeJS 18' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }
        stage('Run NPM Audit') {
            steps {
                echo 'NPM Audit for security vulnerabilities...'
                sh 'npm audit --audit-level=moderate'
            }
        }

        stage('Start Application') {
            steps {
                echo 'Starting the application in background...'
                sh 'nohup npm start &'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build, tests and deploy succeeded!'
        }
        failure {
            echo 'Build or tests or deploy failed.'
        }
    }
}