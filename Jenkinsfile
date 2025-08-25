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
                    script {
                        // Use Docker Compose image to run commands inside
                        docker.image('docker/compose:2.24.1').inside {
                            sh 'docker-compose --version'
                            sh 'docker-compose down || true'
                            sh 'docker-compose build'
                            sh 'docker-compose up -d'
                            sh 'docker-compose ps'
                        }
                }
            }
        }
    }

    post {
        always {
            script {
                docker.image('docker/compose:2.24.1').inside {
                    sh 'docker-compose down'
                }
            }
        }
    }
}
