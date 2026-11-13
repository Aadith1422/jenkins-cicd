
pipeline {
    agent any

    options {
        skipDefaultCheckout true
    }

    stages {

        stage('Source Code Integration') {
            steps {
                echo 'Fetching source code from GitHub'

                checkout scm

                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo 'Starting Python build process'

                sh '''
                    python3 --version
                    python3 -m venv .venv
                    .venv/bin/pip install -r requirements.txt

                    echo "Build completed successfully"
                '''
            }
        }

        stage('Testing') {
            steps {
                echo 'Starting automated testing'

                sh '''
                    .venv/bin/pytest -v
                '''
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully!'
        }

        failure {
            echo 'CI pipeline failed!'
        }
    }
}
