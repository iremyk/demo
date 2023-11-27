pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        sh './mvnw clean install'
      }
    }
    stage('Sonarqube analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh './mvnw sonar:sonar'
        }
      }
    }
  }
}