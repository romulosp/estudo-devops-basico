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

          echo 'GRAVANDO IMAGEM DOCK HUB'
         

          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          
          }
        }
      }
    }
 stage('RUN Image') {
      steps{
        script {
          echo 'SUBINDO O SISTEMA'
          dockerImage.run()
        }
      }
    }
  }
}