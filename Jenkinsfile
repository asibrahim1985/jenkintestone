pipeline {
	//agent { docker {image 'maven:3.6.3'} }
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_TAG - $env.BUILD_TAG"
			}
		}
	}
}

