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
				build 'PetClinic-Compile'
			}
		}
	}
}
