pipeline {
    agent none
    stages {
        stage('Test') {
            agent {
                docker { image 'halamap/publisher-cli:0.0.1'
                         args '--privileged'
                       }
            }
            steps {
                echo 'hello world !'
                sh 'ie-app-publisher-linux'
            }
        }
    }
}
