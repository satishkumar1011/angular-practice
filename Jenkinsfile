pipeline {
    agent any
    environment {
        PROJECT_ID = 'oceanic-catcher-395616'
                CLUSTER_NAME = 'angular-cluster'
                LOCATION = 'us-central1'
                CREDENTIALS_ID = 'practice1'
    }
    
    stages {
        stage("app install"){
            steps{
                sh 'npm install'
            }
            
        }
    stage("build"){
        steps{
            sh 'npm run build'
        }
        
    }
    stage("Docker build"){
       steps{
             sh 'docker version'
             sh 'docker build -t ngapp-test .'
       // sh 'docker image list'
             sh 'docker tag  ngapp-test satish1011/ngapp-test'
             withCredentials([string(credentialsId: 'DOCKER_HUB_SECRET', variable: 'PASSWORD')]) {
             sh 'docker login -u satish1011 -p $PASSWORD'
    }
       }
    }
    
    stage("Push Image to Docker Hub"){
        steps{
             sh 'docker push  satish1011/ngapp-test'
        }
    } 
    
    stage('Deploy to K8s') {
            steps{
                echo "Deployment started ..."
                sh 'ls -ltr'
                sh 'pwd'
                sh "sed -i 's/ngapp-test:latest/ngapp-test:${env.BUILD_ID}/g' test-deployment.yml"
                step([$class: 'KubernetesEngineBuilder', \
                  projectId: env.PROJECT_ID, \
                  clusterName: env.CLUSTER_NAME, \
                  location: env.LOCATION, \
                  manifestPattern: 'deployment.yaml', \
                  credentialsId: env.CREDENTIALS_ID, \
                  verifyDeployments: true])
                }
            }
        }        
}
