pipeline {
    agent {
        docker { image 'halamap/publisher-cli:0.0.3'
        args '--privileged'
                       }
        }
    environment {
        HOME = '.'
    }
    stages {
        stage('Test') {
            
            steps {
                sh 'ls'
                echo 'hello world!'
                sh 'ie-app-publisher-linux -h'
 
            }
        }
    }
}
 
