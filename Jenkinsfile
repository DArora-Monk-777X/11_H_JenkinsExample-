node {
    checkout scm
    docker.image('docker:18.09-dind').withRun() { c ->
        
        docker.image('hello-world').inside("--link ${c.id}:docker") {
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
            sh 'ls'
        }
    }
}
