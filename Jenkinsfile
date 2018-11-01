pipeline {
  agent any
  stages {
    stage('Message') {
      steps {
        echo 'Trial'
      }
    }
    stage('Execute Batch') {
      steps {
        bat 'gradlew,bat'
      }
    }
  }
}