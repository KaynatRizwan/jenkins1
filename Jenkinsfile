pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred')
    }
    stages {
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }
        stage('Test') {
            steps {
                bat 'echo "Test is running"'
            }
        }
        stage('Docker build') {
            steps {
                bat 'docker build -t kainatkhan/jenkins-integration:latest .'
            }
        }
        stage('Login') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
                        bat "echo %DOCKERHUB_PASS% | docker login -u %DOCKERHUB_USER% --password-stdin"
                    }
                }
            }
        }
        stage('Push') {
            steps {
                bat 'docker push kainatkhan/jenkins-integration:latest'
            }
        }
        stage('Deploy') {
            steps {
                bat 'echo "Deploying the application"'
            }
        }
    }
}
