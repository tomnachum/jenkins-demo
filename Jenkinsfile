pipeline {
    agent any // You can specify the node/agent to run the pipeline on

    stages {
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
