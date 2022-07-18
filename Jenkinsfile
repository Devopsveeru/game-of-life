pipeline{
  agent any
    environment {
	  sonar_url = 'http://43.204.227.198:9000/'
	  sonar_admin = 'admin'
	  sonar_password = 'admin@123'
	}  
  stages{
     stage("Maven Build"){
       steps{
            sh "mvn clean package"
        }
    }
     stage('sonar_test') {
       steps{
     withSonarQubeEnv('sonarqube') {
	      sh '''
		  mvn -e -B sonar:sonar -Dsonar.java.source=1.8 -Dsonar.host.url="${sonar_url}" -Dsonar.login="${sonar_admin}" -Dsonar.password ="${sonar_password}"
		  '''
          }
        }		   
        }
    }
}          
