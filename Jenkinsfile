pipeline {
    agent any

    stages {
        /*
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                
                node --version
                npm --version
                npm ci
                npm run build
                ls -la build | grep 'index.html'
                '''
            }
        }
        */
        stage('test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                test -f build/index.html
                npm test                
                '''
            }
        }
        stage('test'){
            agent{
                docker{
                    image 'mcr.microsoft.com/playwright:v1.47.2-noble'
                    reuseNode true
                }
            }
            steps {
                sh '''
                 npm install -g serve
                 serve -s build
                 npx playright test               
                '''
            }
        }
    }
    
}
