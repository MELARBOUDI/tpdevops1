pipeline {
    agent any   // Exécute sur n’importe quel agent disponible

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

