pipeline {
  environment {
    registry = "gustavoapolinario/docker-test"
    registryCredential = 'romulosp-docker-hub'
    dockerImage = ''
  }
  agent any
  stages {
   
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$VERSAO_APLICACAO"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$VERSAO_APLICACAO"
      }
    }
  }
}