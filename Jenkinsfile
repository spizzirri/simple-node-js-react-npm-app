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
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
