pipeline {
    agent any
    environment {
        PATH = "/opt/homebrew/bin:$PATH" // Add Homebrew to Jenkins's PATH
    }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Security Tests') {
            steps {
                sh 'npm test'
            }
        }
    }
}

