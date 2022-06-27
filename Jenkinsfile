pipeline {
    agent { docker { image 'python:3.10.1-alpine' } }
    stages {
        stage('Deploy - Staging') {
            steps {
                echo 'Deploy Staging'
            }
        }

        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }

        stage('Deploy - Production') {
            steps {
                echo 'Deploy production'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'main.py', fingerprint: true
        }
    }
}
