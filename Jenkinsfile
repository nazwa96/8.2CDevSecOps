pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Security Tests') {
            steps {
                sh 'npm audit --json'
            }
        }
    }
}

