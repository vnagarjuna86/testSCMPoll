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
                    sh 'echo "Naga test'
                }
            }
        }
         post {
        always {
            // Cleanup steps to be executed regardless of condition
            
            // Copy command if changes were made to a file
            script {
                if (changeset) {
                    sh 'cp file1 file2'
                }
            }
        }
    }
    
    // Condition to trigger the post section only when changes are made to a file
    when {
        changeset "git"
    }
}

}
