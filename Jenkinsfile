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
                sh 'mkdir ~/.npm-global'
                sh 'npm config set prefix '~/.npm-global'
		sh 'export PATH=~/.npm-global/bin:$PATH'
		sh 'source ~/.profile'
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
