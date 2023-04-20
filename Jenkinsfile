pipeline {
    agent any
    tools {
        jdk 'JDK 8'  // Replace with the correct JDK version available in your Jenkins instance
        maven 'Maven'
        ansible 'Ansible' // Replace with the name you used when defining the Ansible installation
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/r2999xu/my-spring-petclinic.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'ansible-playbook -i /ansible/inventory.ini /ansible/playbook.yml'
            }
        }
    }
}
