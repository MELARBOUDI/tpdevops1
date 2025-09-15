pipeline {
    agent { label 'Agent_Docker' }

    stages {
  	 stage('Test Docker') {
            steps {
                sh 'which docker'
                sh 'docker --version'
                 } 

        }
    }
}

