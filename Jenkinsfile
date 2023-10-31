pipeline {

    agent any

    environment {
        PATH='/usr/local/bin:/usr/bin:/bin'
	}

    stages {

       stage('Install node modules') {
          steps {
             sh 'npm install'
         }
       }

       stage('Build') {
          steps {
             sh 'npm run ng -- build'
             
          }
       }

      // stage('Stage Web Build') {
        //  steps {
          //    sh 'npm run build --prod'
       //   }
      // }

      
}
}
