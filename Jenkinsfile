pipeline {
    agent any

    tools {
        nodejs 'NodeJS' // Make sure this tool is configured in Jenkins → Global Tool Config
    }

    environment {
        ARTIFACT_NAME = 'app.zip'
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
        stage('Package App') {
            steps {
                sh 'zip -r $ARTIFACT_NAME .'
            }
        }

        stage('Publish Artifact') {
            steps {
                archiveArtifacts artifacts: "${ARTIFACT_NAME}", fingerprint: true
            }
        }
    }
}
