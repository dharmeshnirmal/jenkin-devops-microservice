pipeline{
	agent any
	environment  {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages{
		stage('Build'){
			steps{
				sh "mvn --version"
				sh "docker version"
				echo "PATH - $PATH"
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
