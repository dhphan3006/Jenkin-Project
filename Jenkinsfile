pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                // Check if there is index.html file in build directory
                echo 'Test stage'
                sh 'test -f build/index.html'
                // run npm test command
                sh 'npm test'
            }
        }
    }
}
