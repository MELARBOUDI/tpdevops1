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
			agent { label 'Agent_Kube ' } 
		 	steps {
			 script {	
				sh 'minikube kubectl -- apply -f tpdevops.yaml -n tpdevops'
				sh 'minikube kubectl -- rollout status deployment/tpdevops -n tpdevops --timeout=120s' //waiting deploy started 
				sh 'BUILD_ID=dontKillMe screen -dmS toto "minikube kubectl -- -n tpdevops port-forward --address 0.0.0.0 service/tpdevops 8082:80" '
    			 }
			}
		}
		stage('Deploy Dim') {
			agent { label 'Agent_dim ' } 
		 	steps {
			 script {
				 
				sh 'minikube kubectl -- apply -f tpdevops.yaml -n tpdevops'
				sh 'minikube kubectl -- rollout status deployment/tpdevops -n tpdevops --timeout=120s' //waiting deploy started 
				withEnv(['BUILD_ID=dontKillMe']) { sh 'minikube kubectl --  -n tpdevops port-forward --address 0.0.0.0 service/tpdevops 8082:80 &' }
    			 }
			}
		}
	}		
}
