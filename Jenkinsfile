pipeline{
	agent { docker { image 'maven:3.6.3'} }
	stages{
		stage('Build'){
			steps{
				sh "mvn --version"
				echo "Build"
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Int Test'){
			steps{
				echo "Int Test"
			}
		}
	} 
	post{
		always {
			echo "I will run always"
		}
		success {
			echo "I will run when success"
		}
		failure {
			echo "I will run when failure"
		}
	}
}
