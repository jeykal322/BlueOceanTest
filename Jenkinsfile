pipeline {
  agent any
  stages {
    stage('Message') {
      steps {
        echo 'Trial'
      }
    }
    stage('Build') {
      steps {
        bat 'gradlew.bat compileJava'
      }
    }
    stage('Run Tests') {
      steps {
        bat 'gradlew.bat test'
      }
    }
    stage('Archiving artifacts') {
      steps {
        archiveArtifacts '*.log'
      }
    }
  }
  post {
    always {
      archiveArtifacts(artifacts: 'build/libs/**/*.jar', fingerprint: true)
      junit 'build/test-results/**/TEST*.xml'

    }

  }
}