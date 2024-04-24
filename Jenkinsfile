pipeline {
	agent any
	stages {
		stage ('Git_Checkout'){
			steps {
				echo 'Checked  out code from Git Repo';
				git branch: 'main', credentialsId: 'personal_token', url: 'https://github.com/CSPR1999/Scripted_Pipeline.git';
			}
		}
		
		stage ('Build'){
			steps {
				echo 'Executing Build';
			    sh './Build.sh';    
				
			}
		}
		
		stage ('Unit'){
			steps {
				echo 'Executing Unit test';
				sh './Unit.sh'
			}
		}
		
		stage ('Quality'){
			steps {
				echo 'Maintaining Quality Gate';
				sh './Quality.sh'
			}
		}
		
		stage ('Deploy'){
			steps {
				echo 'Deploying the project';
				sh './Deploy.sh'
			}
		}
	}
	post{
		always {
			echo 'This will always run'
		}
		success {
			echo 'This will run only if successfull'
		}
		failure {
			echo 'This will run only if failed'
		}
		unstable {
			echo 'This will run only if the run was marked as unstable'
		}
		changed {
			echo 'This will run only if the state of the Pipeline has changed'
			echo 'Eg: if the pipeline was previously failing but is now successful'
		}
	}
	
}
