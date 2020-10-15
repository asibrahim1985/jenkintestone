pipeline {
	//agent { docker {image 'maven:3.6.3'} }
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
				sh "PATH - $PATH"
				sh "BUILD_NUMBER - $env.BUILD_NUMBER"
				sh "BUILD_TAG - $env.BUILD_TAG"
			}
		}
	}
}

