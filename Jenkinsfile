pipeline {
    agent any
    stages {
        stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/19127577-19127441-19127558/docker_test.git'
			}
		}
        stage ("Build") {
            steps {
		bat "docker build -t jenkins-docker:latest ."
		bat "docker tag jenkins-docker:latest pdtien19/jenkins-docker:latest"
            }
        }
        stage ("Publish") {
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
