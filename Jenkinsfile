pipeline {
    agent Agent_Docker   // Exécute sur serveur docker

    stages {
        stage('Build') {
            steps {
                echo "TESTTTTTTTTTTTT1 !"
                sh 'echo "DATE TEST : $(date)"'
            }
        }

        stage('Environment') {
            steps {
                sh 'printenv'  
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminé (succès ou échec).'
        }
    }
}

