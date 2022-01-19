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
		bat "docker build -t test:latest ."
		bat "docker tag test:latest pdtien19/test:latest"
            }
        }
        stage ("Publish") {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: ''){
                    bat 'docker push pdtien19/test:latest'
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
