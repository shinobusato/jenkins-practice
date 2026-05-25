pipeline {
  agent any

  environment {
    IMAGE_NAME = "jenkins-practice"
  }
  parameters {
    choice(name: 'ENV', choices: ['dev', 'stg'])
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
        script {
          if (params.ENV == 'dev') {
            sh 'echo Deploy to DEV'
          } else {
            sh 'echo Deploy to STG'
          }
        }
      }
    }
  }
}
