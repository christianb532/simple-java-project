pipeline {
  agent any
  stages {
    stage('Cleaning workspace') {
      steps {
			echo 'cleaning workspace...'	  
			sh 'mvn clean'
      }
    }
	stage('Compile') {
      steps {
			echo 'Compiling project...'				  
			sh 'mvn compile'
            }
    }
	stage('Test') {
      steps {
			echo 'Executing Unit tests...'			
			sh 'mvn test'			
      }
    }	
	stage('Sonar Qube') {
      steps {
			echo 'Executing SonarQube...'
			withSonarQubeEnv('sonar'){
				sh 'env'
				sh 'mvn sonar:sonar -Dsonar.login=${SONAR_AUTH_TOKEN}'
			}			
      }
    }
  }
}
b47a043380553596e8d6e45f5ed8331428fefab0