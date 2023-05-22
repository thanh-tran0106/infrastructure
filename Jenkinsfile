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
          sh 'docker volume create artifactory-data'
          sh 'docker pull releases-docker.jfrog.io/jfrog/artifactory-pro:latest'
          sh 'docker run -d --name artifactory -p 8082:8082 -p 8081:8081 -v artifactory-data:/var/opt/jfrog/artifactory releases-docker.jfrog.io/jfrog/artifactory-pro:latest'
          sh 'docker ps -a'
        }
      }
    }
  }
}
}
