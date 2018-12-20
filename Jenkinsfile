pipeline {
    agent any
    stages {
	    stage('Buld') {
			steps{
				echo 'Bulding'
			}
		}
		stage('Parallel Tests') {
			parallels {
				stage('Test 1') {
					steps {
						echo 'Testing'
					}
				}
			},{
				stage (Test 2) {
					steps {	
						echo 'Parallel step'
					}
				}
			}
		stage('Deploy') {
			steps {
				echo 'Deploying'
			}
		}	
	}
}