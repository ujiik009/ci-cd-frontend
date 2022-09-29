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
                script{
                    echo "Deploy is done"
                }
            }
        }
    }
}