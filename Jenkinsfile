pipeline {
	agent { docker {image: '3.6.3'} }
	stages {
		stage('Build') {
			echo 'Build'
			sh 'mvn --version'
		}
	}
}
