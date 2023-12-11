pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('checking docker images') {
            steps {
                sh 'docker images'
            }
        }
        stage('checking docker containers') {
            steps {
                sh 'docker ps -a'
            }

        }
    }
}
