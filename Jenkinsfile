pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3005:3000' 
        }
    }
    triggers {
        pollSCM '*/1 * * * *'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install && npm run build' 
            }
        }
        stage('Test') { 
            steps {
                sh 'npm run test' 
            }
        }
    }
}
