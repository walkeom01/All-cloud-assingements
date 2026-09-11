pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/walkeom01/cloud_assingment_02.git',
                    branch: 'main'
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
            deleteDir()
        }
    }
}
