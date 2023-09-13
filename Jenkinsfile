pipeline {
    agent {
        docker { image 'python_with_pytest:latest' }
    }
    environment {
        PATH = "/usr/bin:$PATH" // Add the directory where Python and pip are located
    }

    stages {
        stage('Install Python3') {
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

        stage('Install pip ') {
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
                sh 'python3 -m pip install pytest'
            }
        }

        stage('Run unit tests in parallel'){
                parallel {
            stage('Run unit tests') {
                steps {
                    // Specify the Python interpreter and run your tests
                    sh 'python3 -m pytest ./test_add.py'
                }
            }
            stage('Run unit tests 2') {
                steps {
                    // Specify the Python interpreter and run your tests
                    sh 'python3 -m pytest ./test_add.py'
                }
            }
        }

        }


    }
}
