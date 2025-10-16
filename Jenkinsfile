pipeline {
    agent any
    environment {
        PATH = "~/.nvm/versions/node/v22.20.0/bin/:$PATH"
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                /var/lib/jenkins/.nvm/versions/node/v22.20.0/bin/node -v
                /var/lib/jenkins/.nvm/versions/node/v22.20.0/bin/npm -v
                npm config set registry http://registry.npm.taobao.org
                npm install
                npm run build
                '''
            }
        }
    }
}