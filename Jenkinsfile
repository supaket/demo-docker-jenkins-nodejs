pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                node
            }
            steps {
                sh 'npm install'
            }
        }
    }
}