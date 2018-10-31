pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradlew.bat clean'
      }
    }
    stage('Message') {
      steps {
        echo 'Hello there'
      }
    }
  }
}