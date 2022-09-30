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
                sh "docker rm -f frontend"
                sh 'docker run -p 8888:80 -d --name frontend frontend:latest'
            }
        }
        stage('Deploy Production') {
            steps {
                echo 'Deploying only because this commit is tagged...',
                script {                                                    
                    if (env.TAG_NAME) {                                       
                        echo "triggered by the TAG:"                                 
                        echo env.TAG_NAME                                       
                    } else {                                                  
                        echo "triggered by branch, PR or ..."                              
                    }                                                         
                }    
            }
        }
        
    }
}