pipeline {
    agent any
    environment {
<<<<<<< HEAD
        PATH = "/opt/homebrew/bin:$PATH" // Ensure snyk is in path
=======
        PATH = "/opt/homebrew/bin:$PATH"
>>>>>>> 334ad94f9860e121a72153f2e4411e20218c12ab
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
                sh "snyk auth $SNYK_TOKEN"
                sh 'npm test'
            }
        }
    }
}
