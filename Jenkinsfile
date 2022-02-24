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
			}
		}
}