# LAB304

pipeline {
    agent any

    stages {
        stage('Pull Docker Image') {
            steps {
                sh "ssh root@192.168.0.7 'docker pull gearpawarit/frontend:${Tag}'"
                
            }
        }
        stage('Check Docker Images') {
            steps {
                sh "ssh root@192.168.0.7 'docker images'"
            }
        }
        
    }
}