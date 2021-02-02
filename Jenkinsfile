node {
    checkout scm
    withEnv(['HOME=.']) {
        stage ('Build') {
             docker.image('docker:18.09-dind').withRun(""" --privileged  """) { c ->
                docker.image('docker:18.09-dind').inside(""" --link ${c.id}:db  """) {
            /* Wait until mysql service is up */
          
                 
                }
             docker.image('halamap/publisher-cli:0.0.3').inside(""" --link ${c.id}:db --privileged -v /workspace:/app/src/workspace --name mycon  """) {
  
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
          
                sh 'ie-app-publisher-linux -h'
                sh """
                    docker exec mycon ls
                    ls -a
                    cd src
                    docker-compose --host tcp://db:2375 build
                    docker --host tcp://db:2375 images
                    cd ..
                    cp -RT src ./workspace
                    cd workspace
                    echo "deploying app..."
                    ie-app-publisher-linux de c -u http://db:2375
                    export IE_SKIP_CERTIFICATE=true
                    ie-app-publisher-linux em li -u "$IEM_URL" -e $USER_NAME -p $PSWD
                    ie-app-publisher-linux em app cuv -a $APP_ID -v $APP_VERSION -y ./docker-compose.prod.yml -n '{"matrix":[{"name":"matrix","protocol":"HTTP","port":"80","headers":"","rewriteTarget":"/"}]}' -s 'matrix' -t 'FromBoxReverseProxy' -u "matrix" -r "/"
                    ie-app-publisher-linux em app uuv -a $APP_ID -v $APP_VERSION
                """
             }
                
          }
        }
    }
}
