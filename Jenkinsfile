pipeline {
    agent { docker { image 'nginx:1.22-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'echo "build"'
            }
        }
    }
}