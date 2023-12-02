pipeline {
  agent { label 'linux' }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('romulosp-docker-hub')
  }
  stages {
    stage('Build') {
      steps {
        sh './jenkins/build.sh'
      }
    }

}