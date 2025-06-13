pipeline {
    agent any


    stages {

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
                bat 'start /B npm start'
            }            
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                bat 'npm test'
            }
        }
        
        stage('Deploy Application to Production') {
            steps {
                echo 'Deploying the application...'
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