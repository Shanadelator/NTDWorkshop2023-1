pipeline {
    agent any
    stages {
        stage('Build container') {
            steps {
                sh 'docker build . -t siimraak/movie-api'
            }
        }
    }
}
