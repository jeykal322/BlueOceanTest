pipeline {
  agent any
  stages {
    stage('Message') {
      steps {
        echo 'Trial'
      }
    }
    stage('Execute Script') {
      steps {
        bat 'gradlew.bat test'
      }
    }
  }
  post {
    always {
        junit 'build/reports/**/*.xml'
    }
  }
}