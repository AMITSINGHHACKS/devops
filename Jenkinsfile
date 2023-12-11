pipeline {
    agent any
    stages {
        stage('checking docker images') {
            steps {
                sh 'sudo docker images -a'
            }
        }
        stage('checking docker containers') {
            steps {
                sh 'sudo docker ps -a'
            }

        }
    }
}
