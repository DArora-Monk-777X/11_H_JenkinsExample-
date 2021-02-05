pipeline {
    agent any

    
    environment {
        VERSION = ""
        NUMBER = 1
    }
    stages {
        stage('Deploy') {
            steps {
                echo 'Building..'
                sh 'ie-app-publisher-linux --version'
                sh 'docker --version'
                sh 'docker-compose --version'
                echo 'Deploy stage executing ...'
          
                script {
                    if (env.BUILD_NUMBER < 10 && env.BUILD_NUMBER > 0) {
                        environment {
                            VERSION = "0.0." // overrides pipeline level NAME env variable
                            NUMBER = "1" // overrides the default BUILD_NUMBER
                        }
                       echo "$VERSION$BUILD_NUMBER/$NUMBER"
                    } else {
        
                    }
                
                sh '''
                    ls
                    rm -rf workspace
                    mkdir workspace
                    cd workspace
                    ls
                    ie-app-publisher-linux ws init
                    cd ..
                    cp -RT src ./workspace
                    cd workspace
                    ie-app-publisher-linux de c -u http://localhost:2375
                    export IE_SKIP_CERTIFICATE=true
                    ie-app-publisher-linux em li -u "$IEM_URL" -e $USER_NAME -p $PSWD
                    ie-app-publisher-linux em app cuv -a $APP_ID -v 0.0.$BUILD_NUMBER -y ./docker-compose.prod.yml -n '{"hello-edge":[{"name":"hello-edge","protocol":"HTTP","port":"80","headers":"","rewriteTarget":"/"}]}' -s 'hello-edge' -t 'FromBoxReverseProxy' -u "hello-edge" -r "/"
                    ie-app-publisher-linux em app uuv -a $APP_ID -v 0.0.$BUILD_NUMBER
                '''

            }
        }
      
    }
}
