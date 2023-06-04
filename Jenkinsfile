pipeline {
    agent any
    stages {
        stage('Build API container') {
            steps {
                sh 'docker build . -t masterman/movie-api'
            }
        }
        stage ('Run API container') {
            steps {
                sh ' docker run -p 3000:3000 --network bridge --name api-container --rm -d masterman/movie-api'
            }
        }
        stage('Build Test container') {
            steps {
                sh 'docker build tests -t masterman/movie-api-tests'
            }
        }
        stage('Execute tests') {
            steps {
                sh 'docker run -e PORT=3000 -e BASE_URI=172.17.0.2 --network bridge -v --rm masterman/movie-api-tests'
            }
        }
        stage('Cleanup') {
            steps {
                sh 'docker kill api-container'
            }
        }
    }
}