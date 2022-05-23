pipeline {
    agent {
        dockerfile {
            
            filename 'dockerfile'
        }
    }
    stages {
        stage ('Build and test') {
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
        stage ('Compile') {
            steps {
              sh '''export GOPATH=$WORKSPACE/go
                export PATH="$PATH:$(go env GOPATH)/bin"               
                go get github.com/tools/godep
                go get github.com/smartystreets/goconvey
                go get github.com/GeertJohan/go.rice/rice  
                go get github.com/wickett/word-cloud-generator/wordyapi
                go get github.com/gorilla/mux
                sed -i "s/1.DEVELOPMENT/1.$BUILD_NUMBER/g" static/version
                GOOS=linux GOARCH=amd64 go build -o ./artifacts/word-cloud-generator -v 
                md5sum artifacts/word-cloud-generator
                ls -l artifacts/
                gzip -f ./artifacts/word-cloud-generator'''   
            }
        }
    }
}
