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
        stage('Build again') {
          steps {
            bat 'gradlew.bat build'
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
        readFile 'gradle/wrapper/gradle-wrapper.jar'
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