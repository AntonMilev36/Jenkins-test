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
                        // Report success to GitHub
                        setGitHubPullRequestStatus context: 'CI/Jenkins', status: 'SUCCESS'
                    } catch (err) {
                        // Report failure to GitHub
                        setGitHubPullRequestStatus context: 'CI/Jenkins', status: 'FAILURE'
                        throw err
                    }
                }
            }
        }
    }
}
