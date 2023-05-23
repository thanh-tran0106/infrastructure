pipeline {
  agent {
     label "robot3"
   }
  stages {
    stage('Checkout: infrastructure source code') {
      steps {
        dir('infrastructure') {
          git branch : 'main',
            url : 'https://github.com/thanh-tran0106/infrastructure.git'
        }     
      }
    }
  
  stage('Jfrog provisioning') {
    steps {
      script {
        dir('infrastructure') {
          sh 'ls -la'
          sh 'sudo docker pull releases-docker.jfrog.io/jfrog/artifactory-oss:latest'
          sh 'sudo docker run --name artifactory -v artifactory-data:/var/opt/jfrog/artifactory -d -p 8081:8081 -p 8082:8082 releases-docker.jfrog.io/jfrog/artifactory-oss:latest'
          sh 'sudo docker ps -a'
        }
      }
    }
  }
}
}
