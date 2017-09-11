pipeline {
  agent any
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
    stage('docker push') {
      steps {
        sh '''docker login -u meetagoyal -p -------
docker push meetagoyal/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}