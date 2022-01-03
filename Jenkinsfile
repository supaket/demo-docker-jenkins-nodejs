pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    label 'node'
                }
            }
            steps {
                sh 'npm install'
            }
        }
    }
}