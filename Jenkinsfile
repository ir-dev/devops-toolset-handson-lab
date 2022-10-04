pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
				echo 'Building..'
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
				echo 'Testing..'
                sh 'npm test' 
            }
        }
		stage('Deploy') {
            steps {
                echo 'Deploying....'
				sh 'docker build -t fhv/devops_lab .'
				sh 'docker container rm -f devops_lab_app'
				sh 'docker run -d --name devops_lab_app -p 7070:3000 fhv/devops_lab'
            }
        }
    }
}