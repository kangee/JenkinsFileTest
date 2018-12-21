pipeline {
    agent any
	parameters {
		booleanParam(name: 'SEND_RESULT_TO_EVERYONE', defaultValue: false, description: 'Should result be sent to everyone?')
	}
    stages {
		stage('Pre Build setup') {
			steps{
				echo 'Seting up release proccess'
			}
		}
		stage('Crating related stuff') {
			steps{
				echo 'Creating all tags if not exists'
			}
		}
	    stage('Build') {
			steps{
				echo 'Building'
			}
		}
		stage('Parallel Tests') {
			parallel {
				stage('Linux CLI tests') {
					steps {
						echo 'Testing linux CLI'
					}
				}
				stage ('Windows CLI Tests') {
					steps {	
						echo 'testing Windows CLI'
					}
				}
				stage ('UI Tests') {
					steps {	
						echo 'Testing the UI'
					}
				}
				stage ('PC lint') {	
					stages {
						stage ('PC lint tests') {	
							steps{
								echo 'PC lint tests'
							}
						}
						stage ('Upload result') {
							steps {
								echo 'upload result'
							}
						}
					}
				}
				stage ('python CLI tests') {
					steps {	
						echo 'python tests'
					}
				}
			}
		}
		stage('Upload if Proper release') {
			steps {
				echo 'Uploading'
			}
		}
		stage('Notify users') {
			steps {
				echo 'Emailing every one'
				build job: 'TOOL-2798EmailTest', parameters: [[$class: 'BooleanParameterValue', name: 'SEND_TO_ALL', value: ${params.SEND_RESULT_TO_EVERYONE}]]
			}
		}	
	}
}