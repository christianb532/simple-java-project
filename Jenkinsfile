pipeline {
  agent any
  stages {
	stage('SCM') {
      steps {
			echo 'checkout from SCM...'	  
			checkout scm
      }
    }
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
	stage('Unit Test') {
      steps {
			echo 'Executing Unit tests...'			
			sh 'mvn test'			
      }
    }	
	stage('Code Analysis') {
      steps {
			echo 'Executing SonarQube...'
			withSonarQubeEnv('sonar'){
				sh 'env'
				sh 'mvn sonar:sonar -Dsonar.login=${SONAR_AUTH_TOKEN}'
			}			
      }
    }
	stage('Code Security') {
      steps {
			echo 'Executing Fortify...'			
      }
    }
  }
}