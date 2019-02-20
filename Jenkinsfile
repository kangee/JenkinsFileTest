
ConfluencePageId=''

pipeline {
    agent any
	parameters {
		string(name: 'RELEASE_NUMBER', defaultValue: '', description: 'The release number for this release.')
		string(name: 'CONFLUENCE_PAGE_ID', defaultValue: '', description: 'The confluence page assosiated with this release, if empty tries to create a new page.')
	}
    stages {
		stage('geting build user'){
			steps {
				wrap([$class: 'BuildUser']) {
				  sh 'echo "${BUILD_USER}"'
				}
			}
		}
	}	
}