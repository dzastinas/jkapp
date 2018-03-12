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
            sh './gradlew check'
          }
        }
        stage('Publish tests') {
          steps {
            junit 'build/reports/**/*.xml'
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