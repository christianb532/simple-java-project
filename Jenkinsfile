pipeline {
  agent any
  stages {
	stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH=${PATH}"
					echo "JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/bin"
					echo "MAVEN_HOME=/usr/share/maven"
                    echo "M2_HOME=/usr/share/maven"
                '''
            }
        }
    stage('Compile') {
      steps {        
          sh 'mvn clean compile'
      }
    }
	stage('Test') {
      steps {        
          sh 'mvn test'
      }
    }	
  }
}