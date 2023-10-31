node{
    
    stage("Git Clone"){

        git branch: 'main', credentialsId: 'GIT_HUB_CREDENTIAL', url: 'https://github.com/satishkumar1011/angular-practice.git'
    }
    stage("app install"){
        bat 'npm install'
        
    }
    stage("build"){
        bat 'npm run build'
        
    }
    stage("Docker build"){
        bat 'docker version'
        bat 'docker build -t ngapp-test .'
        bat 'docker image list'
        bat 'docker tag  ngapp-test satish1011/ngapp-test'
    }
    
    /* withCredentials([string(credentialsId: 'DOCKER_HUB_SECRET', variable: 'PASSWORD')]) {
        bat 'docker login -u satish1011 -p $PASSWORD'
    }


    stage("Push Image to Docker Hub"){
        bat 'docker push  satish1011/ngapp-test'
    } */

    stage("SSH Into k8s Server") {
        def remote = [:]
        remote.name = 'minikube'
        remote.host = '127.0.0.1'
        remote.allowAnyHosts = true

        /* stage('Put k8s-spring-boot-deployment.yml onto k8smaster') {
            sshPut remote: remote, from: 'k8s-spring-boot-deployment.yml', into: '.'
        } */

        stage('Deploy ang app') {
           bat 'kubectl apply -f test-deployment.yml'
        }
    }

}
