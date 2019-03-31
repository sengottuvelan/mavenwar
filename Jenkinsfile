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
        stage ('archive artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
        stage('Deliver') {
            steps {
                //sh 'ansible-playbook ansibledeploy.yml'
                sh 
                build job: 'deploytotomcat'
            }
        }
    }
}
