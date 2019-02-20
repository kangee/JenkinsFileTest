
ConfluencePageId=''

pipeline {
    agent any
	parameters {
		booleanParam( name: 'DIST_TO_ALL', defaultValue: false, description: 'Select if the result of this build should be sent to this dist email list: Dist_All@arccore.onmicrosoft.com')
	}
    stages {
		stage('geting build user'){
			steps{
				script{
					if (params.DIST_TO_ALL) {
						echo 'I only execute on the master branch'
						email = 'markus.fridolfsson@gmail.com'
					} else {
						echo 'I execute elsewhere'
						wrap([$class: 'BuildUser']) {
						  email = BUILD_USER_EMAIL
						}
					}
					
					mail 
					body: """ Sending an email""",
					replyTo: "${BUILD_USER_EMAIL}", subject: 'test', to: "${email}"
					
				}
			}
		}
	}	
}