pipeline {
    agent any
    stages {
        stage('install-pip-deps') {
            steps {
                echo "Installing all required dependencies.."
            }
        }

        stage('deploy-to-dev') {
            steps {
                echo "Deploying to DEV environment..."
            }
        }

        stage('tests-on-dev') {
            steps {
                echo "Running API tests on DEV..."
            }
        }
    }
}