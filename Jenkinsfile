pipeline {
    agent any
    environment {
        PATH = "/opt/homebrew/bin:$PATH" // Make sure Jenkins can find npm and node
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/nazwa96/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true' // Continue even if tests fail
            }
        }

        stage('Generate Coverage Report') {
            steps {
                sh 'npm run coverage || true'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                sh 'npm audit || true'
	   }
        }

        stage('SonarCloud Analysis') {
            steps {


                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    sh """
                        npx sonar-scanner \
                          -Dsonar.projectKey=nazwa96_8.2CDevSecOps \
                          -Dsonar.organization=nazwa96 \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=https://sonarcloud.io \
                          -Dsonar.login=$SONAR_TOKEN
                    """
                }
            }
        }
    }
}
