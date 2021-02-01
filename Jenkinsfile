pipeline {
    agent {
        docker { image 'halamap/publisher-cli:0.0.3' }
    }
    stages {
        stage('Test') {
            steps {
                echo 'hello world !'
                sh 'ie-app-publisher-linux'
            }
        }
    }
}
