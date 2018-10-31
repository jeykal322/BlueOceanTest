pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradlew.bat'
      }
    }
    stage('Message') {
      steps {
        echo 'Hello there'
      }
    }
  }
}