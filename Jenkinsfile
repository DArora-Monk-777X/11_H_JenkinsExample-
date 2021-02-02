node {
    checkout scm
    docker.image('docker:18.09-dind') { c ->
        docker.image('docker:18.09-dind').inside("--link ${c.id}:db") {
          
        }
        docker.image('halamap/publisher-cli:0.0.3').inside("--link ${c.id}:db") {
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
            sh 'make check'
        }
    }
}
