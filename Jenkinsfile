pipeline {
    agent any


	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/khairusyaidy/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP Dependency-Check Vulnerabilities') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', 
				nvdCredentialsId: 'nvd-api-key',
				odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
				
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}