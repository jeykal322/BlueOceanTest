pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradlew.bat test'
      }
    }
    stage('Message') {
      steps {
        echo 'Hello there'
      }
    }
  }
}