pipeline{

    agent any
    stages{
        stage('Build'){
            steps {
                sh 'npm install'
                // sh 'echo "test is is running"'

            }
        }
        stage('test'){
            steps {
                sh 'echo "testing the application'
            }
        }
        stage('deploy'){
            steps {
                sh 'echo "deploying the application"'
            }

        }
    }
}
