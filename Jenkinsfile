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
		PATH = "$myDocker/bin:$myMaven/bin:$PATH"
	}
	stages {
		stage('Build') {
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