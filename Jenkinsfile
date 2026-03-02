pipeline {
  agent any

  environment {
    IMAGE_NAME = "nest-app"
    CONTAINER_NAME = "nest-container"
  }

  stages {

    stage('Build & Test Inside Node Container') {
      steps {
        script {
          docker.image('node:20').inside {
            sh 'npm install'
            sh 'npm run test'
            sh 'npm run build'
          }
        }
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
        docker stop $CONTAINER_NAME || true
        docker rm $CONTAINER_NAME || true
        docker run -d -p 3000:3000 --name $CONTAINER_NAME $IMAGE_NAME
        '''
      }
    }
  }
}