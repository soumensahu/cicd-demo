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
						sendMail("build successfully")
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

def sendMail(status){
	emailext ( 
	attachLog: true,
	body: 'testing mail .please dont reply', 
	subject: 'Build+$env.BUILD_NUMBER - " + $status',
	to: 'soumensahu2011@gmail.com')

}