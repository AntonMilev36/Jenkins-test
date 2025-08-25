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
                        setGitHubPullRequestStatus(
                            context: 'CI/Jenkins',
                            state: 'SUCCESS',
                            description: 'Tests passed',
                            targetUrl: env.BUILD_URL
                        )
                    } catch (err) {
                        setGitHubPullRequestStatus(
                            context: 'CI/Jenkins',
                            state: 'FAILURE',
                            description: 'Tests failed',
                            targetUrl: env.BUILD_URL
                        )
                        throw err
                    }
                }
            }
        }
    }
}