pipeline {

    agent any

    tools{
        
        nodejs 'node'
        
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
