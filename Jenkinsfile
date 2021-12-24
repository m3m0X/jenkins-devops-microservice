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
	//agent any
	agent {
		docker { image 'maven:3.6.3' }
	}
	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
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