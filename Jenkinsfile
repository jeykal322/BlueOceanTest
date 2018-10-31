pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradlew.bat build'
      }
    }
    stage('Message') {
      steps {
        echo 'Hello there'
      }
    }
  }
}