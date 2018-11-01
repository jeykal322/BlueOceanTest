pipeline {
  agent any
  stages {
    stage('Message') {
      steps {
        echo 'Trial'
      }
    }
    stage('Execute script') {
      steps {
        sh 'sudo ./gradlew'
      }
    }
  }
}