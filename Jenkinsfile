pipeline {
  environment {
    registry = "romulosp/estudo-devops-basico"
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
 
  }
}