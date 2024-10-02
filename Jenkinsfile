pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                ls -la build | grep 'index.html'
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('test'){
            steps{
                sh '''
                npm test
                '''
            }
        }
    }
}
