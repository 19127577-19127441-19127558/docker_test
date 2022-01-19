pipeline {
    agent any
    stages {
        stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/tken02/test_docker.git'
			}
		}
        stage ("Build Docker Image and Tag") {
            steps {
		bat "docker build -t jenkins-docker:latest ."
		bat "docker tag jenkins-docker:latest pdtien19/jenkins-docker:latest"
            }
        }
        stage ("Publish to Docker Hub") {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: ''){
                    bat 'docker push pdtien19/jenkins-docker:latest'
            }
        }
        }
    }

    post {
		always {
			bat 'docker logout'
		}
	}

}
