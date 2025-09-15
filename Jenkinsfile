pipeline {
    agent { label 'Agent_Docker' }

    stages {
        stage('Test2') {
            agent {
                docker {
                    image 'python:3.11'
                }
            }
            steps {
                sh 'python --version'
            }
        }
    }
}

