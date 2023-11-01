pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                sh 'docker build -t laravdocker4 .'
                sh 'docker run laravdocker4 php artisan test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker push laravdocker4'
                sh 'docker-compose up -d'
            }
        }
    }
}
