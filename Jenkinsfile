pipeline{

    agent any
    stages{
        stage('Build'){
            steps {
                bat 'npm install'
                // sh 'echo "test is is running"'

            }
        }
        stage('test'){
            steps {
                bat 'echo "testing the application'
            }
        }
        stage('deploy'){
            steps {
                bat 'echo "deploying the application"'
            }

        }
    }
}
