pipeline {
    agent any
    stages {
	    stage('Buld') {
			steps{
				echo 'Bulding'
			}
		}
		stage('Test') {
			steps {
				echo 'Testing'
			},
			{
				echo 'Testing in line'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying'
			}
		}	
	}
}