pipeline {
    agent {
        docker {
            image 'node:latest'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mkdir /tmp/.npm-global'
                sh 'npm config set prefix \'/tmp/.npm-global\''
		sh 'export PATH=/tmp/.npm-global/bin:$PATH'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
