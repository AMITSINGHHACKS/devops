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
        stage('Stopping existing containers') {
            steps {
                sh 'docker stop website'
            }
        }
        stage('remove image') {
            steps {
                sh 'docker rmi -f website'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t website .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -it -d --name website:v2 -p 8082:80 website'
            }
        }
    }
}
