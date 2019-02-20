
ConfluencePageId=''

pipeline {
    agent any
	parameters {
		booleanParam( name: 'DIST_TO_ALL', defaultValue: false, description: 'Select if the result of this build should be sent to this dist email list: Dist_All@arccore.onmicrosoft.com')
	}
    stages {
		stage('geting build user'){
			environment {
				email=''
			}
			steps{
			
				script{
					wrap([$class: 'BuildUser']) {
						if (params.DIST_TO_ALL) {
							echo 'I only execute on the master branch'
							env.email = 'markus.fridolfsson@gmail.com'
						} else {
							echo 'I execute elsewhere'
							
							  env.email = BUILD_USER_EMAIL
							
						}
					}
				}
				mail bcc: '',
						body: '''Hello from jenkins''',
						replyTo: "${BUILD_USER_EMAIL}", subject: 'test', to: "markus.fridolfsson@gmail.com",
						cc: '', from: ''
			}
		}
	}	
}