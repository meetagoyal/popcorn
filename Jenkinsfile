pipeline {
  agent any
  
  environment {
    Docker_password = credentials('Docker_password')
  }
  
  stages {
    stage('greeting') {
      steps {
        sh 'echo "hello world"'
      }
    }
    stage('testing') {
      steps {
        sh 'run rails test'
      }
    }
    
    stage('build docker/add container') {
      steps {
        sh 'docker build -t meetagoyal/popcorn:$BUILD_NUMBER .'
      }
    }
    stage('docker push') {
      steps {
        sh '''docker login -u meetagoyal -p $Docker_password
docker push meetagoyal/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}