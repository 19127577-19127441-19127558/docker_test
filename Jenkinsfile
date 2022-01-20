pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker hub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/19127577-19127441-19127558/docker_test.git'
			}
		}

		stage('Build') {

			steps {
				bat 'docker build -t phamduytien1805/node-app:latest .'
			}
		}

		stage('Login') {

			steps {
				bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push phamduytien1805/node-app:latest'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}
