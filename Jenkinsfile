pipeline{

	agent any
	
		stages{
			stage('Build with Unit Testing'){
				steps {
					script {
						echo 'building'
						bat(/mvn clean install/)
					}
				}
				post {
					success {
						echo "build successfull and sendng mail"
					}
				}
			}
			stage('Integration Test'){
				steps {
					script {
						echo 'integration testing'
						bat(/mvn verify -Dunit-tests.skip=true/)
					}
					// cucumber reports collection
                cucumber buildStatus: null, fileIncludePattern: '**/cucumber.json', jsonReportDirectory: 'target', sortingMethod: 'ALPHABETICAL'
				}
			}
		}
}