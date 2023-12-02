pipeline {
  agent {  label 'master' }
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
    stage('Login') {
      steps {
        sh './jenkins/login.sh'
      }
    }
    stage('Push') {
      steps {
        sh './jenkins/push.sh'
      }
    }
  }
  post {
    always {
      sh './jenkins/logout.sh'
    }
  }
}