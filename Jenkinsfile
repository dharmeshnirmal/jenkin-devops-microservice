pipeline{
	agent any
	environment  {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages{
		stage('Checkout'){
			steps{
				sh "mvn --version"
				sh "docker version"
				echo "PATH - $PATH"
				echo "Build"
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Int Test'){
			steps{
				sh "mvn failsafe:intigration-test failsafe:verify"
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
