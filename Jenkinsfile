pipeline {

    agent any
    
    stages {
        stage("build"){
            steps {
                echo 'Construindo a imagem no docker hub...'
                echo "romulosp/estudo-devops-basico:${env.VERSAO_APLICACAO}"

                script {
                  def customImage = docker.build("romulosp/estudo-devops-basico:${env.VERSAO_APLICACAO}")
                  customImage.push()
                }
            }
        }
        
     stage("deploy"){
            steps {
              echo 'FAZENDO O DEPLOY DA APLICAÇÃO'
              echo "romulosp/estudo-devops-basico:${env.VERSAO_APLICACAO}"


            }
    }
    stage("test"){
            steps {
                echo 'testing the application...'
            }
        }
   
    }
}