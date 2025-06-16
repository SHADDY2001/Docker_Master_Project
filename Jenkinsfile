pipeline {
  agent any

  environment {
    IMAGE_NAME = "shaddy100601/docker-master-project"
  }

  stages {
    stage('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/SHADDY2001/Docker_Master_Project.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Push to Docker Hub') {
      steps {
        withDockerRegistry(credentialsId: 'dockerhub-creds', url: '') {
          sh 'docker push $IMAGE_NAME'
        }
      }
    }
  }
}
