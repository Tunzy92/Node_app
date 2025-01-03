pipeline{
    agent any 
        environment {
            DOCKERHUB_CREDENTIALS=credentials('dockerhub')
        }
    stages {
        stage ('Git clone') {
            steps {
                git 'https://github.com/Tunzy92/Node_app.git'
            }
        }
        stage ('Build') {
            steps {
                sh 'docker build -t tunzy/node-app:latest .'
            }
        }
        stage ('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage ('Push') {
            steps {
                sh 'docker push tunzy/node-app:latest'
            }
        }
    }
}
