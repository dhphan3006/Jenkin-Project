pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh '''
                    npm install
                    npm run build
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Verifying the index.html file exists...'
                sh '''
                    if [ -f build/index.html ]; then
                        echo "File index.html exists in the build directory."
                    else
                        echo "File index.html does not exist in the build directory."
                        exit 1
                    fi
                '''
            }
        }
    }
}
