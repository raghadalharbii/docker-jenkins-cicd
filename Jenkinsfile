pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('New-docker-hup-Access')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t raghaddevops/dojo-jump:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push  raghaddevops/dojo-jump:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}