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
            def testImage = docker.build("dockerfile", "--net ${mynet}")
            }
            steps {
                sh '''
                make lint && make test
                 if [ $? -ne 0 ];
                    then
                        echo "Test error"
                        exit 1
                    fi
                '''
            }
        
        }
    }
}
