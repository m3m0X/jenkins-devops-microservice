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
	// agent { docker { image 'maven:3.8.4' } }
	agent { docker { image 'node:17.3' } }
	stages {
		stage('Build') {
			steps {
				// sh 'mvn --version'
				sh 'node --version'
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