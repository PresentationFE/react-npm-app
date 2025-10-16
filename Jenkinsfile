pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                node -v
                npm -v
                npm config set registry http://registry.npm.taobao.org
                npm install
                npm run build
                '''
            }
        }
    }
}