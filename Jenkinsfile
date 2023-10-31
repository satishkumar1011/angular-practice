pipeline {

    agent any

    tools{
        
        node 'nodejs18.16.1'
        
    }

    environment {
        PATH='/usr/local/bin:/usr/bin:/bin'
	}

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/satishkumar1011/angular-practice.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }
        stage('Deploy to Conatiner') {
            steps {
                sh "npm run compose:up -d"
            }
        }
        
    }
}
