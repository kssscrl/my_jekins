pipeline{
    agent any
    tools {
        jdk 'my_jdk'
        maven 'my_maven'
    }

    stages{
      
       stage('Build'){
            steps{
                sh 'sudo ./mvnw clean install'
            }
         }

        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        	steps{
       	 withSonarQubeEnv('Sonarqube-10.0') { 
       		sh "./mvnw sonar:sonar"
    	}
               }
        }
       
    }	
}
