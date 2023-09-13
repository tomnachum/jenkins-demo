pipeline {
    agent any

    stages {
        stage('Install Python') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'sudo apt-get update -y && sudo apt-get install -y python3'
                    } else {
                        bat 'choco install python --version 3.x'
                    }
                }
            }
        }

        stage('Install pip') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'sudo apt-get update -y && sudo apt-get install -y python3-pip'
                    } else {
                        bat 'choco install python --version 3.x'
                    }
                }
            }
        }

        stage('Install pytest') {
            steps {
                // Make sure pip is in the PATH
                sh 'python -m pip install pytest'
            }
        }

        stage('Run unit tests') {
            steps {
                // Specify the full path to the Python interpreter and run your tests
                sh '/usr/bin/python3 ./test_add.py' // Use the full path to Python
            }
        }
    }
}
