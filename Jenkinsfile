pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'ie-app-publisher-linux --version'
                sh 'docker --version'
                sh 'docker-compose --version'
                echo 'Deploy stage executing...'
          
                sh '''
                    ls
                    cd workspace
                    ls
                    ie-app-publisher-linux ws init
                    cd ..
                    cp -RT src ./workspace
                    cd workspace
                    ie-app-publisher-linux de c -u http://localhost:2375
                '''

            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
