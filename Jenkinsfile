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
			withSonarQubeEnv(credentialsId: 'b47a043380553596e8d6e45f5ed8331428fefab0', installationName: 'sonar'){
				sh 'mvn sonar:sonar'
			}			
      }
    }
  }
}