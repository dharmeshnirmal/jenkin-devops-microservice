pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
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
