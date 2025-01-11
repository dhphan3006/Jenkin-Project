pipeline {
    agent any

    stages {
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
                //sh 'test -f build/index.html'
                // run npm test command
                //sh 'npm test'
            }
        }
    }
}
