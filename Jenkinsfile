pipeline {
  agent any
  stages {
    stage('Message') {
      parallel {
        stage('Message') {
          steps {
            echo 'Trial'
          }
        }
        stage('error') {
          steps {
            echo 'pls no'
          }
        }
      }
    }
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            bat 'gradlew.bat compileJava'
          }
        }
        stage('error') {
          steps {
            bat 'gradlew.bat compileJava'
          }
        }
        stage('error') {
          steps {
            echo 'asd'
          }
        }
      }
    }
    stage('Run Tests') {
      parallel {
        stage('Run Tests') {
          steps {
            bat 'gradlew.bat test'
          }
        }
        stage('error') {
          steps {
            bat 'gradlew.bat build'
          }
        }
        stage('error') {
          steps {
            echo 'awawaw'
          }
        }
        stage('error') {
          steps {
            timeout(time: 33) {
              echo 'Time limit was reached and this should fail'
            }

          }
        }
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
      parallel {
        stage('Another msg') {
          steps {
            echo 'eh'
          }
        }
        stage('Something') {
          steps {
            pwd(tmp: true)
          }
        }
      }
    }
    stage('sleep') {
      steps {
        sleep(unit: 'MILLISECONDS', time: 500)
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