//SCRIPTED

//DECLARATIVE
pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHmoe/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {				
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}

		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}

		stage('Test') {
			steps {				
				sh "mvn test"
			}
		}

		stage('Integration Test') {
			steps {				
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps {				
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker Image') {
			steps {
				//"docker Build -t in28min/currency-exchage-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.Build("in28min/currency-exchage-devops:${env.BUILD_TAG}")
				}
			}
		}
	
		stage('Push Docker Image') {
			steps {
				//"docker Build -t in28min/currency-exchage-devops:$env.BUILD_TAG"
				script {
					docker.withRegistry('', 'dockerhub' ) {
						dockerImage.Push()
						dockerImage.Push('latest')
					}
				}
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