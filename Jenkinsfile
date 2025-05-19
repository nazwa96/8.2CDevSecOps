pipeline {
    agent any
    environment {
        PATH = "/opt/homebrew/bin:$PATH" // Ensure snyk is in path
        SNYK_TOKEN = credentials('SNYK_TOKEN')
    }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Security Tests') {
            steps {
                sh 'snyk auth $SNYK_TOKEN'
                sh 'npm test'
            }
        }
    }
}

