node {
    def root = tool name: 'hello', type: 'go'
    ws("${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}/src/github.com/teratipallysaitej/yo") {
        withEnv(["GOROOT=${root}", "GOPATH=${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}/", "PATH+GO=${root}/bin"]) {
            env.PATH="${GOPATH}/bin:$PATH"
            
            stage 'Checkout'
        
            git url: 'https://github.com/teratipallysaitej/yo.git'
        
            stage 'preTest'
            sh 'go version'
            sh 'go get -u github.com/golang/dep/...'
            sh 'dep init'
            
            
            stage 'Build'
        sh 'git clone https://github.com/teratipallysaitej/yo.git'
        sh 'cd yo'
        sh 'go build ./hello.go'
        sh 'ls'
        
        sh 'curl -fL https://getcli.jfrog.io | sh'
        
        sh './jfrog'
        sh './jfrog rt u hello example-repo-local/ --user=admin --password=password --url=http://192.168.99.100:8081/artifactory'

 

        //sh './hello.exe"
           // sh 'go run hello.go'
            echo 'SUCCESSFUL BUILD of GOLANG APPLICATION'
            
           // stage 'Deploy'
            // Do nothing.
        
        }
    }
}
