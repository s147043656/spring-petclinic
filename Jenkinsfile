pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
//				git url: gitUrl
				sh 'mvn -B compile'
			}
		}
		stage('Test') {
			steps {
//				git url: gitUrl
				sh 'mvn -B verify'
				junit '**/target/surefire-reports/*.xml'
				archiveArtifacts '**/target/*.war'
			}
		}
	}
}
