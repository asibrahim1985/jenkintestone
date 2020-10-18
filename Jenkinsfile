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
		stage('Build Jar') {
			steps {
				sh 'mvn clean install'
			}
		}
		stage('Build Image') {
			steps {
				//docker -t build -t asibrahim/asimosiprepo:test-jenkins-1.0.0
				script {
					dockerImage = docker.build("asibrahim/asimosiprepo:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Image') {
			steps {
				//docker -t build -t asibrahim/asimosiprepo:test-jenkins-1.0.0
				script {
					docker.withRegistry('','dockerhub') {
						dockerImage.push()
					}
					
				}
			}
		}
		stage('Deploy Image') {
			steps {
				withKubeConfig([credentialsId: 'kubmasternode', serverUrl: '161.97.120.67']) {
					script { 
						sh 'kubectl version'
					}
				}
			}
		}
	}
}

