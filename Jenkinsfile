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
          sh 'docker pull releases-docker.jfrog.io/jfrog/artifactory-oss:latest'
          sh 'docker run -d --name artifactory -p 8082:8082 -p 8081:8081 -v releases-docker.jfrog.io/jfrog/artifactory-oss:latest'
          sh 'docker ps -a'
        }
      }
    }
  }
}
}
