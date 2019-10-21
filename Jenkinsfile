pipeline {
  agent any
  stages {
    stage('Cleaning workspace') {
      steps {
			echo 'cleaning workspace...'	  
			sh 'mvn clean'
			post{
				success {
						echo 'cleaning workspace... Success'
				}
                failure {
						echo 'cleaning workspace... Failure'
				}				
				aborted {
						echo 'cleaning workspace... Aborted'
				}

            }
      }
    }
	stage('Compile') {
      steps {
			echo 'Compiling project...'
				  
			sh 'mvn compile'
			post{
				success {
						echo 'Compiling project... Success'
						
				}
                failure {
						echo 'Compiling project... Failure'
						
				}				
				aborted {
						echo 'Compiling project... Aborted'
						
				}

            }

      }
    }
	stage('Test') {
      steps {
			echo 'Executing Unit tests...'
			
			sh 'mvn test'			
			post{
				success {
						echo 'Executing Unit tests... Success'
						
				}
                failure {
						echo 'Executing Unit tests... Failure'
						
				}				
				aborted {
						echo 'Executing Unit tests... Aborted'
						
				}

            }
      }
    }	
	stage('Sonar Qube') {
      steps {
			echo 'Executing SonarQube...'
			
			sh 'mvn sonar:sonar'			
			post{
				success {
						echo 'Executing SonarQube...... Success'
						
				}
                failure {
						echo 'Executing SonarQube...... Failure'
						
				}				
				aborted {
						echo 'Executing SonarQube...... Aborted'
						
				}

            }
      }
    }
  }
}