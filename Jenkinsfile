@Library('piper-lib-os') _
try {
    node() {
        stage('prepare') {
            checkout scm
            setupCommonPipelineEnvironment script:this
        }
        stage('build') {
            mtaBuild script: this
        }
        stage('deploy') {
            cloudFoundryDeploy script: this
        }
    }
} finally {
	node {
		mailSendNotification script: this
	}
}
