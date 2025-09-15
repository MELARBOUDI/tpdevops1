pipeline {
    agent { label 'Agent_Docker' }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
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
    }
}
 
