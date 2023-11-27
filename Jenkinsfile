pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sonarqube') {
          withMaven(maven:'Maven 3.9.5') {
              sh 'mvn clean package sonar:sonar'
          }
        }
      }
    }
  }
}