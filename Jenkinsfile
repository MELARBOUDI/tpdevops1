pipeline {
    agent { label 'Agent_Docker' }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'luksor',
                    url: 'https://github.com/MELARBOUDI/tpdevops1.git'
            }
        }
    }
}
