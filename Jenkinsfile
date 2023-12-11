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
	stage('stopping unwanted containers') {
            steps {
                sh 'docker stop website1'
            }
        }
	stage('Pruning') {
            steps {
                sh 'docker container prune -f'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -it -d --name website1 -p 8082:80 website'
            }
        }
    }
}
