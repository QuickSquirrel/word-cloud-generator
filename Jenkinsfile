pipeline {
    agent {
        docker {
            image 'node:7-alpine'
            args '-v jenkins_data:/var/lib/jenkins/workspace'
        }
    }
    stages {
        stage ('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}
