pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
    }
    tools {
        nodejs 'NodeJS'
    }
    stages {
        stage('Checkout from Git') {
            steps {
                git branch: 'main', url: 'https://github.com/luckysuie/msdocs-nodejs-mongodb-azure-sample-app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('package app') {
            steps {
                sh 'zip -r app.zip .'
            }
        }
        stage('publish the artifact') {
            steps {
                archiveArtifacts artifacts: 'app.zip', fingerprint: true
            }
        }
    }
}