pipeline {
  environment {
    registry = "romulosp/estudo-devops-basico"
    registryCredential = 'romulosp-docker-hub'
    dockerImage = ''
  }
  agent any
  stages {
   
    stage('CONSTRUINDO IMAGEM DOCKER') {
      steps{
        script {
          dockerImage = docker.build registry + ":$VERSAO_APLICACAO"
        }
      }
    }
    stage('Deploy IMAGEM DOCKER') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
 
  }
}