pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            
        }
        stage('Deliver') {
            steps {
                //sh 'ansible-playbook ansibledeploy.yml'
                build job: 'deploytotomcat'
            }
        }
    }
}
