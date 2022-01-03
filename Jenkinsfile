pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                label docker
            }
            steps {
                sh 'npm install'
            }
        }
    }
}