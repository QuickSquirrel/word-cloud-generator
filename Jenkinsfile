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
        
            stage ('Test') {
            agent {
                dockerfile { filename 'dockerfile' 
                            args '--net final_nginx-net'
                           }
            }
            }
            
        }
    }
}
