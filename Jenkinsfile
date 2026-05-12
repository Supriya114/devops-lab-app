pipeline {
    agent any

    tools {
        nodejs 'NodeJS-18'
    }

    stages {

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Run') {
            steps {
                sh 'node app.js'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline Failed!'
        }
    }
}
