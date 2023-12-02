pipeline {

   agent {
        docker { image 'node:20.10.0-alpine3.18' }
    }
    
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
              cho 'FAZENDO O DEPLOY DA APLICAÇÃO'
              sh  "docker run -d -p 80:80 romulosp/estudo-devops-basico:${env.VERSAO_APLICACAO}"
            }
      }
      
    stage("test"){
            steps {
                echo 'testing the application...'
            }
        }
   
    }
}