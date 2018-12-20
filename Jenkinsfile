pipeline {
    agent any
    stages {
	    stage('Buld') {
			steps{
				echo 'Bulding'
			}
		}
		stage('Test') {
			parallels {
				echo 'Testing'
			},{
				echo 'Parallel step'
			}
		stage('Deploy') {
			steps {
				echo 'Deploying'
			}
		}	
	}
}