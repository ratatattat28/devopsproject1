pipeline {
  environment {
    registry = “ratatattat28/nginx-frontend”
    registryCredential = ‘dockerhub_id’
    dockerImage = ‘nginx-frontend’
  }
  agent any
  stages {
    stage(‘Cloning Git’) {
      steps {
        git ‘https://github.com/ratatattat28/devopsproject1.git '
      }
    }
    stage(‘Building image’) {
      steps{
        script {
          dockerImage = docker.build registry + “:$BUILD_NUMBER”
        }
      }
    }
    stage(‘Deploy Image’) {
      steps{
        script {
          docker.withRegistry( ‘’, registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
