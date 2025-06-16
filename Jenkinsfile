pipeline {
  agent any

  stages {
    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("shaddy100601/Docker-Master-Project")
        }
      }
    }

    stage('Push to Docker Hub') {
      steps {
        withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
          script {
            dockerImage.push()
          }
        }
      }
    }
  }
}
