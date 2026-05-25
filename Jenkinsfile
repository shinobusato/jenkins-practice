pipeline {
  agent any

  environment {
    IMAGE_NAME = "jenkins-practice"
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Run Test') {
      steps {
        sh 'docker run --rm $IMAGE_NAME'
      }
    }

    stage('Deploy') {
      steps {
        sh 'echo Deploying...'
      }
    }
  }
}
