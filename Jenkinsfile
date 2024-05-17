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
                    // Assuming DOCKERHUB_CREDENTIALS is a single entry in the format "username:password"
                    def dockerHubCredentials = env.DOCKERHUB_CREDENTIALS.split(':')
                    def dockerHubUsername = dockerHubCredentials[0]
                    def dockerHubPassword = dockerHubCredentials[1]
                    bat "echo ${Applecat@93} | docker login -u ${kainatkhan} --password-stdin"
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
