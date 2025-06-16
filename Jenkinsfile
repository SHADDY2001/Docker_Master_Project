pipeline {
  agent {
    docker { image 'docker:latest' }
  }

  environment {
    DOCKER_IMAGE = 'shadab100601/docker-master-project'
  }

  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/SHADDY2001/Docker_Master_Project.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("${DOCKER_IMAGE}")
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
