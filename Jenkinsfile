@Library('piper-lib-os') _
node() {
	stage('prepare') {
		checkout scm
		setupCommonPipelineEnvironment script:this
	}
	stage('build') {
		mtaBuild script: this
	}
	stage('deploy') {
		steps {
			cloudFoundryDeploy script: this
		}
		
		post {
			always {
				mailSendNotification script: this
			}
		}
	}	    
}
