
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
                sh 'docker rmi $(docker images -aq) '
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
        stage('Deploy Image') {
            steps{
               script {
                  docker.withRegistry( 'https://hub.docker.com/repository/docker/truthaniket/jenkinsdevops/', 'dockerhub' ) {
                  dockerImage.push()
                }
              }
            }
        } 
    }
    post {
    always {
        echo 'Slack Notifications'
        slackSend (
            channel: 'pipeline-notifications',
            message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} \n build ${env.BUILD_NUMBER} \n More info at: ${env.BUILD_URL}"
        )
        mail bcc: '', body: "Hey the project pipeline is running \n *${currentBuild.currentResult}:* Job ${env.JOB_NAME} \n build ${env.BUILD_NUMBER} ", cc: 'aniketsingh78698@gmail.com', from: '', replyTo: '', subject: 'Jenkins devops', to: 'as216889@gmail.com'
    }
}
}
