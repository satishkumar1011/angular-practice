node{
    
    stage("Git Clone"){

        git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIAL', url: 'https://github.com/satishkumar1011/angular-practice.git'
    }
    stage("app install"){
        sh 'npm install'
        
    }
    stage("build"){
        sh 'npm run build'
        
    }
    stage("Docker build"){
        sh 'docker version'
        //sh 'docker build -t ngapp-test .'
       // sh 'docker image list'
       // sh 'docker tag  ngapp-test satish1011/ngapp-test'
    }
    
    /* withCredentials([string(credentialsId: 'DOCKER_HUB_SECRET', variable: 'PASSWORD')]) {
        sh 'docker login -u satish1011 -p $PASSWORD'
    }


    stage("Push Image to Docker Hub"){
        sh 'docker push  satish1011/ngapp-test'
    } */

    stage("SSH Into k8s Server") {
        def remote = [:]
        remote.name = 'minikube'
        remote.host = '127.0.0.1'
        remote.allowAnyHosts = true

        /* stage('Put k8s-spring-boot-deployment.yml onto k8smaster') {
            sshPut remote: remote, from: 'k8s-spring-boot-deployment.yml', into: '.'
        } */

       /* stage('Deploy ang app') {
           sh 'kubectl apply -f test-deployment.yml'
        }*/
    }

}
