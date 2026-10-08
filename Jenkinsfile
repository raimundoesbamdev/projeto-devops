pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker build -t minha-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f minha-app || true'
                sh 'docker run -d --name minha-app -p 8080:80 minha-app'
            }
        }

    }
}
