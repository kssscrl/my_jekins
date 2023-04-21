pipeline {
    agent any
    tools {
        jdk 'JDK 20'  
        maven 'Maven'
        ansible 'Ansible' 
    }
    
    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/kssscrl/my_jekins.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean install'
            }
        }
        
    stage('Archive JAR file') {
                steps {
                    archiveArtifacts artifacts: 'target/petclinic.jar', fingerprint: true
                }
            }
        
        stage('Deploy Application') {
            steps {
                sh 'ansible-playbook -i inventory.ini playbook.yml -vvv'
            }
        }
    }
}
