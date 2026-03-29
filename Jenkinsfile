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
                script {
                    deployService("dev", "7001")
                }
            }
        }

        stage('tests-on-dev') {
            steps {
                script {
                    runTests("dev")
                }
            }
        }
    }
}

def deployService(envName, port) {
    echo "Deployment to ${envName} environment has started.."
    git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
    bat """
        pm2 delete greetings-app-${envName} || EXIT /B 0        
        python -m venv venv
        .\\venv\\Scripts\\python -m pip install -r requirements.txt
        pm2 start app.py --name greetings-app-${envName} --interpreter "%CD%\\venv\\Scripts\\python.exe" -- --port ${port}
    """
    echo "Deployment to ${envName} finished."
}

def runTests(envName) {
    echo "Testing Python Greetings service has started on ${envName} environment.."
    git branch: 'main', url: 'https://github.com/mtararujs/course-js-api-framework'
    bat """
        npm install
        npm run greetings greetings_${envName}
    """
    echo "Testing on ${envName} finished."
}