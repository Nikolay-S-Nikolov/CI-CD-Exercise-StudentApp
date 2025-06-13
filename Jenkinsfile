pipeline {
    agent any


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
                bat 'npm install'
            }
        }
        stage('Run NPM Audit') {
            steps {
                echo 'NPM Audit for security vulnerabilities...'
                bat 'npm audit --audit-level=moderate'
            }
        }

        stage('Start Application') {
            steps {
                echo 'Starting the application in background...'
                bat 'npm start &'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                bat 'npm test'
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