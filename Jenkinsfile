pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('esmonesan_hub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t esmonesan/app:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push esmonesan/app:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
