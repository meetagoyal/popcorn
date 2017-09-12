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
    
    
    stage('build docker/add container') {
      steps {
        sh 'docker build -t meetagoyal/popcorn:$BUILD_NUMBER .'
      }
    }
    
    stage('testing') {
      steps {
        sh '''docker run meetagoyal/popcorn:$BUILD_NUMBER rails test'''
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