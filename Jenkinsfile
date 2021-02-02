node {
    checkout scm
    docker.image('docker:18.09-dind').withRun('--privileged') { c ->
        docker.image('docker:18.09-dind').inside("--link ${c.id}:db") {
            /* Wait until mysql service is up */
 
        }
        docker.image('halamap/publisher-cli:0.0.3').inside('"--link ${c.id}:db" -e "HOME = '.'"') {
  
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
            sh 'ie-app-publisher-linux -h'
        }
    }
}
