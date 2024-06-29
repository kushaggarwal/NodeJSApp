pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment{
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        APP_NAME = 'webapp'
    }
    stages{
        stage('Build'){
            steps{
                sh 'docker build -t kijebor/$APP_NAME .'
            }
        }
        stage('Login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin' 
            }
        }
        stage('Push'){
            steps{
                sh 'docker push kijebor/$APP_NAME'
            }
        }
        stage('Monitor'){
            steps{
                echo "This is a monitor stage"
            }
        }
    }
}
