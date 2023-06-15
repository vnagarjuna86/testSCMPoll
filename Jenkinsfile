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
                    // Check for changes using the git step
                    def changes = checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vnagarjuna86/testSCMPoll.git']]])
                    if (changes.polling && changes.polling.lastChangeset) {
                        sh '''
                        cat file1
                        echo 'file1 content'
                        cp file1 file2
                        '''
                    }
                }
            }
        }
    }
    
    post {
        always {
            // Cleanup steps to be executed regardless of condition
            echo 'cleanup'
        }
    }
}
