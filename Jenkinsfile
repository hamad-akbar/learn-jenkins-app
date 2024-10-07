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
                
                node --version
                npm --version
                npm ci
                npm run build
                ls -la build | grep 'index.html'
                '''
            }
        }
        stage('running paralel')
        {
            parallel{
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
                npm ci
                npm test                
                '''
            }
        }
        stage('test1'){
            
            steps {
                sh '''
                echo "helow from test1"              
                '''
            }
        }

            }
        }
        
        
            
        
        

    }



}
        
