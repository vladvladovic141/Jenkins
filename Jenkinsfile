pipeline {
    agent any
    stages {
        stage('install-pip-deps') {
            steps {
                echo "Installing all required dependencies.."
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
                bat 'dir'
                script {
                    bat """
                        python -m venv venv
                        .\\venv\\Scripts\\python -m pip install -r requirements.txt
                    """
                }
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