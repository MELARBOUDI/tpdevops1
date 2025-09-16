pipeline {
    agent { label 'Agent_Docker' }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'luksor',
                    url: 'https://github.com/MELARBOUDI/tpdevops1.git'
            }
        }
		stage('Build') {
            steps {
			  script {
               def customImage = docker.build("dretaux/tp_devops:v2")

                /* Push the container to the custom Registry */
                customImage.push()
			  }
            }
        }
		stage('Deploy') {
		 	steps {
			 script {	
				sh 'minikube kubectl -- apply -f tpdevops.yaml -n tpdevops'
				sh 'minikube kubectl -- port-forward --address 0.0.0.0 service/tpdevops 8082:80 &'
    			 }
			}
		}
	}		
}
