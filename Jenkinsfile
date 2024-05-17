// pipeline{

//     agent any
//     stages{
//         stage('Build'){
//             steps {
//                 bat 'npm install'
//                 // sh 'echo "test is is running"'

//             }
//         }
//         stage('test'){
//             steps {
//                 bat 'echo "testing the application'
//             }
//         }
//         stage('deploy'){
//             steps {
//                 bat 'echo "deploying the application"'
//             }

//         }
//     }
// }

pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub') // Add DockerHub credentials in Jenkins
    }

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('myapp')
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKERHUB_CREDENTIALS) {
                        docker.image('myapp').push('latest')
                    }
                }
            }
        }
    }
}
