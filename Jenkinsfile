pipeline {
    agent any

    tools {
        nodejs 'NodeJS-18'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Run') {
            steps {
                sh 'nohup npm start &'
            }
        }
    }

    post {
        success {
            echo 'Pipeline Success!'
        }

        failure {
            echo 'Pipeline Failed!'
        }
    }
}
