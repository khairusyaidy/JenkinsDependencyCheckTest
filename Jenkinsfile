pipeline {
    agent any

    environment {
        // Define your API key as an environment variable
        NVD_API_KEY = credentials('nvd-api-key')  // Use the ID you gave the API key credential
    }


	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/khairusyaidy/JenkinsDependencyCheckTest.git'
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