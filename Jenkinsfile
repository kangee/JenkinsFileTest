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
					steps {	
						echo 'PC lint tests'
						echo 'upload result'
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
			}
		}	
	}
}