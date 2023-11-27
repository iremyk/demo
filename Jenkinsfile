pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Sonarqube analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh 'mvn sonar:sonar'
        }
      }
    }
  }
}