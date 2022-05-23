pipeline {
    agent none
    stages {
        stage('Compile, test, upload to nexus') {
            agent {
                dockerfile { filename 'dockerfile' }
            }
            steps {
                sh 'ls -la'
            }
        }
        stage('Testing') {
            agent {
                dockerfile { filename 'alpine/alpinedockerfile' }
            }
            steps {
                sh 'ls -la'
            }
        }
    }
}
