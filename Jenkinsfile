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
    }
    
    post {
        always {
            // Cleanup steps to be executed regardless of condition
                echo 'cleanup'
            
            script {
                // Check for changes using the git step
                def changes = git(changed: true, poll: false)
                if (changes) {
                    sh 'cp file1 file2'
                }
            }
        }
    }
}
