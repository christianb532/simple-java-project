pipeline {
  agent any
  stages {
	stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
					echo "JAVA_HOME = /usr/bin"
					echo "MAVEN_HOME = /usr/share/maven"
                    echo "M2_HOME = /usr/share/maven"
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