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
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image'){
			steps{
				script {
					dockerImage = docker.build("dharmeshnirmal/currency-exchange-devops:${env.Build_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script {
					docker.withRegistry('','dockerhub'){
						dockerImage.push()
						dockerImage.push('latest')
					}
				}
			}
		}
		stage('Deploy'){
			steps{
				sh "docker run -d -p 8000:8000 --name=currency-exchange dharmeshnirmal/currency-exchange:${env.Build_TAG}"
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
