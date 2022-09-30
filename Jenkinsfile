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
                sh 'echo $TAG_NAME'
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
                sh "docker rm -f frontend"
                sh 'docker run -p 8888:80 -d --name frontend frontend:latest'
            }
        }
        stage('Deploy Production') {
            when { tag "*" }
            steps {
                echo 'Deploying only because this commit is tagged...'
            }
        }
        
    }
}