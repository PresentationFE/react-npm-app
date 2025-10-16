/* groovylint-disable CompileStatic, DuplicateStringLiteral */
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
        stage('Test') {
            steps {
                env.NODE_ENV = 'test'
                print "Environment will be : ${env.NODE_ENV}"
                sh 'node -v'
                sh 'npm prune'
                sh 'npm install'
                sh 'npm run test'
            }
        }

        stage('Build Docker') {
            sh './dockerBuild.sh'
        }

        stage('Deploy') {
            echo 'Push to Repo'
            sh './dockerPushToRepo.sh'

            echo 'ssh to web server and tell it to pull new image'
            // sh 'ssh deploy@xxxxx.xxxxx.com running/xxxxxxx/dockerRun.sh'
        }

        stage('Cleanup') {
            echo 'prune and cleanup'
            sh 'rm node_modules -rf'

            mail body: 'project build successful',
        from: 'feynman.wang@heavengifts.com',
        replyTo: 'feynman.wang@heavengifts.com',
        subject: 'This project build successful',
        to: 'feynman.wang@heavengifts.com'
        }
    }
}
