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
                ls -la /build
                node --version
                npm --version
                npm ci
                npm test
                ls -la
                '''
            }
        }
    }
}
