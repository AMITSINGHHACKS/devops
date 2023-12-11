pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        stage('check images and containers'){
           steps {
sh 'docker ps -a'
}
        }
    }
}
}
