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
    }
}
