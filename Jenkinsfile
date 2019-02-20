
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
					if (DIST_TO_ALL==true) {
						echo 'I only execute on the master branch'
						email = 'markus.fridolfsson@gmail.com'
					} else {
						echo 'I execute elsewhere'
						wrap([$class: 'BuildUser']) {
						  email = BUILD_USER_EMAIL
						}
					}
					echo "${email}"
					echo "${DIST_TO_ALL}"
				}
			}
		}
	}	
}