//SCRIPTED

//DECLARATIVE
pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	stages {
		stage('Build') {
			steps {				
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NIMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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