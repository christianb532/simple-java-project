pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        withMaven(maven: 'maven339', jdk: 'JDK8') {
          sh 'mvn clean install -DskipTests'
        }
      }
    }
  }
}