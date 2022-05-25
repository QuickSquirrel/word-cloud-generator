pipeline {
    agent any
    environment {
        mynet = ' '
    }
    stages {
        stage ('Get neywork docker name') {
           steps {
              sh '''
                 mynet=$(docker network ls | grep nginx | cut --delimiter=' ' -f 4)
              '''
           }
        }
        stage ('Test') {
            agent {
                dockerfile { filename 'dockerfile' 
                            additionalBuildArgs '--build-arg --net "$mynet"'
                            
                }
                steps {
                    sh '''
                     echo $mynet
                    '''
                }
            }
        }
    }
}
