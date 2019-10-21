pipeline {
  agent any
  stages {
	stage('Clone from SCM') {
            steps {             
                echo 'connecting to SCM...'
				updateGitlabCommitStatus name: 'Jenkins build', state: 'running'	  
				checkout scm'
				post{
					success {
							echo 'clone from SCM... Success'
							updateGitlabCommitStatus name: "Jenkins build", state: 'success'
					}
					failure {
							echo 'clone from SCM... Failure'
							updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
					}				
					aborted {
							echo 'clone from SCM... Aborted'
							updateGitlabCommitStatus name: "Jenkins build", state: 'canceled'
					}
					unstable {
							echo 'clone from SCM... Unstable'
							updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
					}

				}
            }
    }
    stage('Cleaning workspace') {
      steps {
			echo 'cleaning workspace...'
			updateGitlabCommitStatus name: 'Jenkins build', state: 'running'	  
			sh 'mvn clean'
			post{
				success {
						echo 'cleaning workspace... Success'
						updateGitlabCommitStatus name: "Jenkins build", state: 'success'
				}
                failure {
						echo 'cleaning workspace... Failure'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}				
				aborted {
						echo 'cleaning workspace... Aborted'
						updateGitlabCommitStatus name: "Jenkins build", state: 'canceled'
				}
				unstable {
						echo 'cleaning workspace... Unstable'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}

            }
      }
    }
	stage('Compile') {
      steps {
			echo 'Compiling project...'
			updateGitlabCommitStatus name: 'Jenkins build', state: 'running'	  
			sh 'mvn compile'
			post{
				success {
						echo 'Compiling project... Success'
						updateGitlabCommitStatus name: "Jenkins build", state: 'success'
				}
                failure {
						echo 'Compiling project... Failure'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}				
				aborted {
						echo 'Compiling project... Aborted'
						updateGitlabCommitStatus name: "Jenkins build", state: 'canceled'
				}
				unstable {
						echo 'Compiling project... Unstable'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}

            }

      }
    }
	stage('Test') {
      steps {
			echo 'Executing Unit tests...'
			updateGitlabCommitStatus name: 'Jenkins build', state: 'running'
			sh 'mvn test'			
			post{
				success {
						echo 'Executing Unit tests... Success'
						updateGitlabCommitStatus name: "Jenkins build", state: 'success'
				}
                failure {
						echo 'Executing Unit tests... Failure'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}				
				aborted {
						echo 'Executing Unit tests... Aborted'
						updateGitlabCommitStatus name: "Jenkins build", state: 'canceled'
				}
				unstable {
						echo 'Executing Unit tests... Unstable'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}

            }
      }
    }	
	stage('Sonar Qube') {
      steps {
			echo 'Executing SonarQube...'
			updateGitlabCommitStatus name: 'Jenkins build', state: 'running'
			sh 'mvn sonar:sonar'			
			post{
				success {
						echo 'Executing SonarQube...... Success'
						updateGitlabCommitStatus name: "Jenkins build", state: 'success'
				}
                failure {
						echo 'Executing SonarQube...... Failure'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}				
				aborted {
						echo 'Executing SonarQube...... Aborted'
						updateGitlabCommitStatus name: "Jenkins build", state: 'canceled'
				}
				unstable {
						echo 'Executing SonarQube...... Unstable'
						updateGitlabCommitStatus name: "Jenkins build", state: 'failed'
				}

            }
      }
    }
  }
}