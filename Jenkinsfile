pipeline {
    agent {
        docker { image 'halamap/publisher-cli:0.0.3' }
    }
    stages {
        stage('Test1') {
            steps {
                sh 'ie-app-publisher-linux -h'
            }
        }
    }
}
