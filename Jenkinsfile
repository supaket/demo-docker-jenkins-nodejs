pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                label 'node'
            }
            steps {
                sh 'npm install'
            }
        }
    }
}