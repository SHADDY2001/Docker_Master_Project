pipeline {
  agent any

  environment {
    IMAGE_NAME = "shaddy100601/docker-master-project"
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/SHADDY2001/Docker_Master_Project.git'
      }
    }

    stage('Build Image') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Login and Push to DockerHub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
          sh '''
            echo "$DOCKERHUB_PASS" | docker login -u "$DOCKERHUB_USER" --password-stdin
            docker push $IMAGE_NAME
          '''
        }
      }
    }
  }
}
