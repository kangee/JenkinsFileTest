

pipeline {
    agent any
	parameters {
		string(name: 'RELEASE_NUMBER', defaultValue: '', description: 'The release number for this release.')
		string(name: 'CONFLUENCE_PAGE_ID', defaultValue: '', description: 'The confluence page assosiated with this release, if empty tries to create a new page.')
	}
    stages {
		stage('Pre Build setup') {
			steps{
				echo 'Seting up release proccess'
				build job: 'TOOL-2799', parameters: [[$class: 'StringParameterValue', name: 'RELEASE_NUMBER', value: params.RELEASE_NUMBER],[$class: 'StringParameterValue', name: 'CONFLUENCE_PAGE_ID', value: params.CONFLUENCE_PAGE_ID]]
				script {
				  // trim removes leading and trailing whitespace from the string
				  params.CONFLUENCE_PAGE_ID = readFile('test.txt').trim()
				}
			}
		}
		stage('Crating related stuff') {
			steps{
				echo 'Creating all tags if not exists'
				echo "${params.CONFLUENCE_PAGE_ID}"
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
				}
		}	
	}
}