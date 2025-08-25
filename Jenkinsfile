pipeline {
    agent any

    tools {
        nodejs "node"
    }

stages {
        stage('Build & Test') {
            steps {
                script {
                    try {
                        sh 'npm install'
                        sh 'npm test'
                        // notify GitHub of success
                        githubNotify context: 'CI/Jenkins', status: 'SUCCESS'
                    } catch (err) {
                        // notify GitHub of failure
                        githubNotify context: 'CI/Jenkins', status: 'FAILURE'
                        throw err
                    }
                }
            }
        }
    }
}
