pipeline {
  agent any
  tools {
        maven 'Maven 3.6.0'
    }
  stages {
	stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
    stage('Compile') {
      steps {        
          sh 'mvn clean install -DskipTests'
      }
    }
  }
}