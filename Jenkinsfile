pipeline {
    agent any
    tools {
        jdk 'my_jdk'
        maven 'my_maven'
    }

    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'my_maven') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('SonarQube analysis') {
            steps {
                withMaven(maven: 'my_maven') {
                    withSonarQubeEnv('Sonarqube-10.0') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }
    }
}
