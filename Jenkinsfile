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
            steps {
                sh 'ls'
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
