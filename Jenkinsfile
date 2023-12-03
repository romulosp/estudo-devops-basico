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

    stage('run image'){
            steps{
                echo "docker run -d -p 127.0.0.1:8081:8081 " + registry + ":$VERSAO_APLICACAO"
                bat "docker run -d -p 127.0.0.1:8081:8081 " + registry + ":$VERSAO_APLICACAO"
            }
    }


  }
}