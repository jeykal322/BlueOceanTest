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
        archiveArtifacts(artifacts: ‘**/*.jar’, fingerprint: true)
      }
    }
  }
  post {
    always {
       steps {
      junit 'build/test-results/**/TEST*.xml'
        }
    }

  }
}