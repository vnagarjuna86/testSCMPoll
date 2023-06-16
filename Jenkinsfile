pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'echo "Naga test"'
                }
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
          
          // Skip the pipeline if the specific file is not modified
          if (!fileChanged) {
            // error('No changes in the specific file. Aborting the build.')
              echo 'file not changed'
          }
          else
            echo 'file changed'
        }
      }
    }
    }
    
    // Add more stages as needed
  }
