pipeline {
    agent any // You can specify the node/agent to run the pipeline on

    stages {

        stage('Install Python') {
            steps {
                // Install Python using the appropriate package manager for your system
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
                // Install pip using the appropriate package manager for your system
                script {
                    if (isUnix()) {
                        sh 'sudo apt-get update -y && sudo apt-get install -y python3-pip'
                    } else {
                        bat 'choco install python --version 3.x'
                    }
                }
            }
        }

        stage('Install pytest ') {
            steps {
                sh 'pip install pytest'
            }
        }

        stage('Run unit tests') {
            steps {
                sh 'python ./test_add.py'
                }
        }
    }
}
