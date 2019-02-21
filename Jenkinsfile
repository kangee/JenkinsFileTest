

RecipiantEmail=''
ArtifactBuildNumber=''

pipeline {
    agent any
	parameters {
		booleanParam( name: 'DIST_TO_ALL', defaultValue: false, description: 'Select if the result of this build should be sent to this dist email list: Dist_All@arccore.onmicrosoft.com')
	}
    stages {
		stage ('Build TOOL-2807'){
			steps{
				script{
					result=build job: 'Tool-2807'
					ArtifactBuildNumber="${result.getNumber}"
				}
			}
		}
		stage('geting build user'){
			steps{
				script{
					wrap([$class: 'BuildUser']) {
						if (params.DIST_TO_ALL) {
							echo 'I only execute on the master branch'
							RecipiantEmail = 'markus.fridolfsson@gmail.com'
						} else {
							echo 'I execute elsewhere'
							
							  RecipiantEmail = BUILD_USER_EMAIL
							
						}
					}
				}
				mail body: '''Hello from jenkins this is link ${ArtifactBuildNumber}''', subject: 'test', to: "${RecipiantEmail}"
			}
		}
	}	
}