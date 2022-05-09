pipeline {
    agent any
    
    tools {
        go 'Go 1.16'
    }
    
    stages {
        stage ("Test compile") {
            steps ("Download and test") {
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
         stage ("Build"){
            steps{
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
        stage ("Upload to nexus") {
            steps {
                nexusArtifactUploader (artifacts: [[artifactId: 'world-cloud-generator', 
                classifier: '', file: 'artifacts/word-cloud-generator.gz', 
                type: 'gz']], credentialsId: 'uploader', groupId: "$git_branch", 
                nexusUrl: 'nexus:8081', nexusVersion: 'nexus3', protocol: 'http', 
                repository: 'world-cloud-build', version: '1.$BUILD_NUMBER')
            }
        }   

        }
        
    }
