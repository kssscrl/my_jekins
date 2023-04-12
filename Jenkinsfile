pipeline{
    agent any
    tools {
        jdk 'my_jdk'
        maven 'my_maven'
    }

    stages{
      
       stage('Build'){
            steps{
                sh 'mvn clean install'
            }
         }

        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        	steps{
       	 withSonarQubeEnv('Sonarqube-10.0') { 
       		sh "mvn sonar:sonar -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=admin -Dsonar.password=YYJyyj317&"
    	}
               }
        }
       
    }	
}
