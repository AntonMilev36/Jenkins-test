pipeline {
    agent any

    tools {
        nodejs "node"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AntonMilev36/Jenkins-test.git'
            }
        }

        stage('Install dependencies') {
            steps { sh 'npm install' }
        }

        stage('Run tests') {
            steps { sh 'npm test' }
        }
    }
}
