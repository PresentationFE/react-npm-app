pipeline {
    agent any
    environment {
        PATH = "/var/lib/jenkins/.nvm/versions/node/v22.20.0/bin/:$PATH"
    }
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