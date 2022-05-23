pipeline {
    agent {
        docker {
            image 'node:7-alpine'
            args '-v jenkins_vol:/var/lib/jenkins/workspace/jenkins'
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
