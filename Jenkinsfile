pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ci-demo-job.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Parallel Tests') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        sh 'npm test'
                    }
                }

                stage('Lint') {
                    steps {
                        sh 'npm run lint'
                    }
                }
            }
        }
    }

    post {
        always {
            sh 'rm -rf *'
        }
    }
}
