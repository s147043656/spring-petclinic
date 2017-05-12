pipeline {
	agent {
		label agent1
	}
	stages {
		stage('Build') {
			agent {
				label agent2
			}
			steps {
				git url: gitUrl
				sh 'mvn -B compile'
			}
		}
		stage('Test') {
			agent {
				label agent2
			}
			steps {
				git url: gitUrl
				sh 'mvn -B verify'
				junit '**/target/surefire-reports/*.xml'
			}
		}
	}
}
