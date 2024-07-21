pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'C:\Users\khair\Documents\Lab\JenkinsDependencyCheckTest'
			}
		}

		stage('OWASP Dependency-Check Vulnerabilities') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}