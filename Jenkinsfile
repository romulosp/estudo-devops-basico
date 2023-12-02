pipeline {
agent any
stages {
        stage('Build image') {
            steps {
                echo 'Starting to build docker image'

                script {
                def customImage = docker.build("romulosp/estudo-devops-basico:v1")
                customImage.push()
                }
            }
        }
        stage('Login') {
                steps {
                    sh './jenkins/login.sh'
                }
        }
    }
}