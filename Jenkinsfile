pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('hub.dockersss')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t zakithereal33888/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push zakithereal33888/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}