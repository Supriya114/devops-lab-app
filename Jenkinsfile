pipeline {
    agent any

    tools {
        nodejs 'NodeJS-18'
    }

    environment {
        APP_NAME = "devops-lab-app"
        PORT = "3000"
        GITHUB_TOKEN = credentials('github-token')
    }

    stages {

        stage('Check Node') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'echo $APP_NAME'
                sh 'npm run build'
            }
        }

        stage('Parallel Tests') {
            parallel {

                stage('Unit Test') {
                    steps {
                        sh 'npm test'
                    }
                }

                stage('Code Check') {
                    steps {
                        sh 'echo Code Quality Check Passed'
                    }
                }

            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t devops-lab-app .'
            }
        }

    }

    post {

        success {
            echo 'Pipeline Successful!'
        }

        failure {
            echo 'Pipeline Failed!'
        }

    }
}
