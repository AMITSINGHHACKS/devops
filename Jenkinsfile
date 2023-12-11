pipeline {
    agent any
    stages {
        stage('checking docker images') {
            steps {
                sh 'docker images -a'
            }
        }
        stage('checking docker containers') {
            steps {
                sh 'docker ps -a'
            }

        }
        stage('checking docker images') {
            steps {
                sh 'docker build -t web2'
            }
        }
        stage('checking docker images') {
            steps {
                sh 'docker images -a'
            }
        }
    }
}
