pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                   ls -la
                   node --version 
                   npm --version
                   npm ci # instead of npm install
                   npm run build
                   ls -la
                '''
            }
        }
        stage("test"){
            steps {
                reuseNode true
                sh '''
                    test -f ./build/index.html
                    npm run test
                '''
                
            }
        }

    }
}

