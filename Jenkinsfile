pipeline {
    agent {
        docker { image 'halamap/publisher-cli:0.0.1' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'ie-app-publisher-linux --version'
            }
        }
    }
}
