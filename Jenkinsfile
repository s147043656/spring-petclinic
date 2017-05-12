pipeline {
    parameters {
        string(defaultValue: "$agent1", description: 'What build agent1?', name: 'agent1')
	string(defaultValue: "$agent2", description: 'What build agent2?', name: 'agent2')
    }
    agent {
	label '${params.agent1}'
	}
    stages {
        stage('Prep') {
        agent {
            label '${params.agent1}'
        }
            steps {
                sh 'echo $JAVA_HOME'
                sh 'echo $MVN_HOME'
                sh 'echo $PATH'
                sh 'pwd'
                sh 'sleep 5'
            }
        }
        stage('Build') {
            agent {
                label 'agent2'
            }
            steps {
		checkout(
		    [$class: 'GitSCM',
    		 branches: [[name: '*/master']],
		     doGenerateSubmoduleConfigurations: false,
	    	 extensions: [],
		     submoduleCfg: [],
	    	 userRemoteConfigs: [[url: 'gitUrl']]]
		)
                sh 'mvn clean package'
            }
        }
    }
}