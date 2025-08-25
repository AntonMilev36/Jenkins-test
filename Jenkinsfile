pipeline {
    agent any

    tools {
        nodejs "node"
    }

stages {
        stage("Build") {
            steps {
                sh 'npm install'
                    }
                }

        stage("Test") {
            steps {
                sh "npm test"
            }
        }

        stage("Image building") {
            steps {
                sh "docker-compose down"
                sh "docker-compose build"
                sh "docker-compose up -d"
            }
        }
    }
}
