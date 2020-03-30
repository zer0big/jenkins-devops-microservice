//SCRIPTED

//DECLARATIVE
pipeline {
	agent { docker { image 'maven:3.6.3'} }
	stages {
		stage('Build') {
			steps {				
				echo "mvn --version"
				echo "Build"
			}
		}
		stage('Test') {
			steps {				
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {				
				echo "Integration Test"
			}
		}
	} 
	post {
		always {
			echo 'I am awesome. I run always'
		}
		success {
			echo 'I run when you are sucessful'
		}
		failure {
			echo 'I run when you are failure'
		}
		changed {
			echo 'I run when you are failure'

		}
	}
}