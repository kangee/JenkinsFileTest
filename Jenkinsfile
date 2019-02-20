
ConfluencePageId=''

pipeline {
    agent any
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