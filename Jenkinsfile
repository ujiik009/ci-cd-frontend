pipeline {
    agent any
    environment {
        DOCKER_IMAGE = ''
    }
    triggers {
        githubPush()
    }  
    stages {
        stage('Init ENV'){
            steps {
                echo 'Init'
                echo '******************************'
            }
        }
        stage('Docker Build') {
            agent any
            steps{
                echo 'Docker Build'
                echo '******************************'
                script {
                  DOCKER_IMAGE = docker.build "frontend:latest"
                }
            }
        }
        stage('Deploy') {
            steps{
                echo 'Deploy'
                echo '******************************'
                sh 'docker run -p 8888:80 -d frontend:latest'
            }
        }
    }
}