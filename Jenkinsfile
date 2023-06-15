pipeline {
  agent any
  
  stages {
    stage('Checkout') {
      steps {
        // Checkout the repository
        //checkout scm
        git remote set-url origin git@github.com:vnagarjuna86/testSCMPoll.git
      }
    }
    
    stage('Check Changes') {
      steps {
        script {
          def fileChanged = false
          // Get the list of changed files between the current and previous commit
          def changedFiles = sh(returnStdout: true, script: 'git diff --name-only HEAD^ HEAD').trim().split('\n')
          
          // Check if the specific file is in the list of changed files
          if (changedFiles.contains('file1')) {
            fileChanged = true
          }
          
          // Abort the pipeline if the specific file is not modified
          if (!fileChanged) {
            error('No changes in the specific file. Aborting the build.')
          }
          else
            echo 'changed'
        }
      }
    }
    
    stage('Build') {
      steps {
        // Perform your build steps here
        echo 'build'
      }
    }
    
    // Add more stages as needed
  }
}
