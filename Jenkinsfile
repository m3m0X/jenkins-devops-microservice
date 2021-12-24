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
	stages {
		stage('Build') {
			steps {
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
	
	pose {
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