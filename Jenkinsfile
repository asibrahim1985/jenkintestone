pipeline {
	//agent { docker {image 'maven:3.6.3'} }
	agent any
	environment {
		dockerHome = tool 'docker'
		mavenHome = tool 'mavenTool'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Initilaize') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_TAG - $env.BUILD_TAG"
			}
		}
		stage('Build') {
			steps {
				sh 'mvn clean install'
			}
		}
	}
}

