pipeline {
    agent { docker { image 'python:3.10.1-alpine' } }
    stages {
        stage('Deploy - Staging') {
            steps {
                sh './deploy staging'
                sh './run-smoke-tests'
            }
        }

        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }

        stage('Deploy - Production') {
            steps {
                sh './deploy production'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'main.py', fingerprint: true
        }
    }
}
