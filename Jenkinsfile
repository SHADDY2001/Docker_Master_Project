pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/SHADDY2001/docker-master-project.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("shaddy100601/docker-master-project")
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
