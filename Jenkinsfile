pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('master') {
            steps {
                sh 'echo master'
            }
        }


        stage('dev') {
            steps {
                sh 'echo dev'
            }
        }
    }
}
