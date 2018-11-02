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
      parallel {
        stage('Archiving artifacts') {
          steps {
            archiveArtifacts(artifacts: '**/*.jar', fingerprint: true)
          }
        }
        stage('Test again') {
          steps {
            bat 'gradlew.bat test'
          }
        }
      }
    }
    stage('Another msg') {
      steps {
        echo 'eh'
      }
    }
    stage('Read my pipeline.log') {
      steps {
        readFile 'pipeline.log'
      }
    }
  }
  post {
    always {
      archiveArtifacts(artifacts: '**/*.jar', fingerprint: true)
      junit 'build/test-results/**/TEST*.xml'

    }

  }
}