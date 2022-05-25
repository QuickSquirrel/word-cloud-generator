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
                 echo $mynet
                 echo "$mynet"
              '''
           
        }
        
        }
    }
}
