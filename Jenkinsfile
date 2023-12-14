@Library('Jenkins_shared_library') _
def COLOR_MAP = [
    'FAILURE' : 'danger',
    'SUCCESS' : 'good'
]
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
    post {
    always {
        echo 'Slack Notifications'
        slackSend (
            channel: 'pipeline-notifications'
            color: COLOR_MAP[currentBuild.currentResult],
            message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} \n build ${env.BUILD_NUMBER} \n More info at: ${env.BUILD_URL}"
        )
    }
}
}
