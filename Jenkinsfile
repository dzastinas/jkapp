pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './gradlew assemble'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            sh './gradlew clean check'
          }
        }
        stage('Publish tests') {
          steps {
            junit 'featureA/build/reports/**/testDebugUnitTest/*.html'
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}