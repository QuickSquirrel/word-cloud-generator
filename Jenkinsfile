pipeline {
    agent {
        docker {
            image 'node:7-alpine'
            args '-v jenkins_vol:/var/lib/jenkins/workspace/jenkinsfile'
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
