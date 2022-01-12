//SCRIPTED
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Test 2"
// 	}
// }


//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.8.4' } }
	//agent { docker { image 'node:17.3' } }
	environment{
		dockerhome = tool "myDocker"
		mavenhome = tool "myMaven"
		PATH = "$dockerhome/bin:$mavenhome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps{
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage('Package') {
			steps {
				sh 'mvn package -DskipTest'
			}
		}
		stage('Build docker image') {
			steps {
				script {
					// docker build -t m3m0cker/repo:$env.BUILD_TAG
					dockerImage = docker.build("m3m0cker/repo:${env.BUILD_TAG}")
				}
				
			}
		}
		stage('Push docker image') {
			steps {
				script {
					docker.withRegistry('','dockerhub'){
						//dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	} 

	post {
		always {
			echo "I am awesome. I run always"
		}
		success {
			echo "Run when success"
		}
		failure {
			echo "Stage Fail!"
		}
	}
}