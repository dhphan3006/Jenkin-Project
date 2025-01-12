pipeline {
    agent any

    stages {
        stage ('Build'){
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
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                // Check if there is index.html file in build directory
                echo 'Test stage'
                sh 'test -f build/index.html'
                // run npm test command
                sh 'npm test'
            }
        }

        stage('E2E') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.49.1-noblee'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    npm install -g serve
                    node_modules/.bin/serve -s build
                    npx playwright test
                '''
            }
        }
    }

    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
