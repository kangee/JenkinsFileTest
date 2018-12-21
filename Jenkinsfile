pipeline {
    agent any
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
				sleep 15
			}
		}
		stage('Parallel Tests') {
			parallel {
				stage('Linux CLI tests') {
					steps {
						echo 'Testing linux CLI'
						sleep 3
					}
				}
				stage ('Windows CLI Tests') {
					steps {	
						echo 'testing Windows CLI'
						sleep 3
					}
				}
				stage ('UI Tests') {
					steps {	
						echo 'Testing the UI'
						sleep 3
					}
				}
				stage ('PC lint') {	
					stages {
						stage ('PC lint tests') {	
							steps{
								echo 'PC lint tests'
								sleep 3
							}
						}
						stage ('Upload result') {
							steps {
								echo 'upload result'
								sleep 3
							}
						}
					}
				}
				stage ('python CLI tests') {
					steps {	
						echo 'python tests'
						sleep 3
					}
				}
			}
		}
		stage('Upload if Proper release') {
			steps {
				echo 'Uploading'
				sleep 15
			}
		}
		stage('Notify users') {
			steps {
				echo 'Emailing every one'
				build job: 'TOOL_2798EMAILTEST', parameters: [[$class: 'BooleanParameterValue', name: 'SEND_TO_ALL', value: false]]
			}
		}	
	}
}