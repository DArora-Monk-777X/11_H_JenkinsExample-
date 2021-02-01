node {
    checkout scm
    
        docker.image('halamap/publisher-cli:0.0.3') {
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
            sh 'ie-app-publisher-linux --version'
        }
}
